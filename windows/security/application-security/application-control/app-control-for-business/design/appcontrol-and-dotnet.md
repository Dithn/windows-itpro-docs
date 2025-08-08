---
title: App Control for Business and .NET
description: Understand how App Control and .NET work together and use Dynamic Code Security to verify code loaded by .NET at runtime.
ms.localizationpriority: medium
ms.date: 03/19/2025
ms.topic: article
---

# App Control for Business and .NET

> [!WARNING]
> When App Control is enforced, .NET doesn't load certain Component Object Model (COM) objects if their registration GUID doesn't match the one calculated by the system at runtime. When that happens, the user sees a general COM load error dialog, but no events or other information is logged to the system. For more information, see [App Control Admin Tips & Known Issues: .NET doesn't load COM objects with mismatched GUIDs](../operations/known-issues.md#net-doesnt-load-component-object-model-com-objects-with-mismatched-guids).

.NET apps (as written in a high-level language like C#) are compiled to an Intermediate Language (IL). IL is a compact code format that can be supported on any operating system or architecture. Most .NET apps use APIs that are supported in multiple environments, requiring only the .NET runtime to run. IL needs to be compiled to native code in order to execute on a CPU, for example Arm64 or x64. When .NET compiles IL to native image (NI) on a device with an App Control user mode policy, it first checks whether the original IL file passes the current App Control policies. If so, .NET sets an NTFS extended attribute (EA) on the generated NI file so that App Control knows to trust it as well. When the .NET app runs, App Control sees the EA on the NI file and allows it.

The EA set on the NI file only applies to the currently active App Control policies. If one of the active App Control policies is updated or a new policy is applied, the EA on the NI file is invalidated. The next time the app runs, App Control will block the NI file. .NET handles the block gracefully and falls back to the original IL code. If the IL still passes the latest App Control policies, then the app runs without any functional issue. Since the IL is now being compiled at runtime, you might notice a slight reduction in performance of the app. When .NET must fall back to IL, .NET will also schedule a process to run at the next maintenance window to regenerate all NI files, thus reestablishing the App Control EA for all code that passes the latest App Control policies.

In some cases, if an NI file is blocked, you might see a "false positive" block event in the *CodeIntegrity - Operational* event log as described in [App Control Admin Tips & Known Issues](../operations/known-issues.md#net-native-images-might-generate-false-positive-block-events).

To mitigate any performance reduction caused when the App Control EA isn't valid or is missing:

- Avoid updating the App Control policies often.
- Run `ngen update` (on all machine architectures) to force .NET to regenerate all NI files immediately after applying changes to your App Control policies.
- Migrate applications to .NET Core (.NET 6 or greater) and enable [Native AOT](/dotnet/core/deploying/native-aot).

## App Control and .NET Dynamic Code Security hardening

Security researchers found that some .NET capabilities that allow apps to load libraries from external sources or generate new code at runtime can be used to circumvent App Control. To address this potential vulnerability, App Control includes an option called *Dynamic Code Security* that works with .NET to verify code loaded at runtime.

When Dynamic Code Security is enabled, your App Control policy is applied to libraries that .NET loads from external or remote sources, like the internet or a network share. It also detects tampering in code generated to disk by .NET and blocks loading code that is tampered. Additionally, some .NET loading features not supported with Dynamic Code Security, including loading unsigned assemblies built with System.Reflection.Emit, are always blocked.

Usually, when dynamic code is blocked, its parent process is stopped or crashes. To prevent this using ASP.NET, you can precompile the dynamic code for deployment only. See ["Precompiling for Deployment Only" in the ASP.NET Precompilation Overview](/previous-versions/aspnet/bb398860(v=vs.100)#precompiling-for-deployment-only).

> [!IMPORTANT]
> .NET Dynamic Code Security works in audit mode only on Windows 11 24H2 and later, and Windows Server 2025 and later. There's no audit mode for Dynamic Code Security on Windows 10, or on earlier versions of Windows 11 and Windows Server. If any App Control policy sets option **19 Enabled:Dynamic Code Security** on those earlier versions, then dynamic code security hardening is *turned on and enforced* even if the policy is in audit mode. Always test your apps thoroughly and  use safe deployment practices when deploying app control policies to production.

Dynamic Code Security mitigates potential attack techniques often referred to as "second order" attacks. That means that the attacker has access to the system and is able to run code. The second order attacks might be attempts to gain persistence or further obscure the attackers activities. Although Dynamic Code Security is important and recommended, Microsoft also recommends testing the policy in audit mode on systems running Windows 11 24H2 and later, or Windows Server 2025 and later before you enforce it.

Code blocked by Dynamic Code Security is logged using event ID 3114 in the **CodeIntegrity - Operational** event log. Except for code loaded using one of the unsupported .NET features like System.Reflection.Emit, you can create rules to allow blocked dynamic code using information from the events. See [Use the App Control Wizard to create rules from the App Control Event Logs](./appcontrol-wizard-parsing-event-logs.md).

> [!NOTE]
> .NET attempts two different methods to run dynamically generated code. If your App Control policy blocks the first method, .NET tries the second one. Each of the two attempts raises a distinct 3114 event. When a 3114 event occurs in isolation, it's safe to ignore as a "false positive" because it only covers the first attempt by .NET to run the code. Only when you see two 3114 events back-to-back within milliseconds for the same code does it indicate an actual issue to review.

To enable Dynamic Code Security, add option **19 - Enabled:Dynamic Code Security** to your App Control policy using the App Control Wizard, the set-ruleoption PowerShell cmdlet, or by adding the following to the `<Rules>` section of your App Control policy XML:

```xml
<Rule>
    <Option>Enabled:Dynamic Code Security</Option>
</Rule>
```
