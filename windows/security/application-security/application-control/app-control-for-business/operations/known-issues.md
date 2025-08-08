---
title: App Control Admin Tips & Known Issues
description: App Control Known Issues
ms.manager: jsuther
ms.date: 03/19/2025
ms.topic: troubleshooting
ms.localizationpriority: medium
---

# App Control Admin Tips & Known Issues

[!INCLUDE [Feature availability note](../includes/feature-availability-note.md)]

This article covers tips and tricks for admins and known issues with App Control for Business. Test this configuration in your lab before enabling it in production.

## Admin tips and hints

### App Control policy file locations

**Multiple policy format App Control policies** are found in the following locations depending on whether the policy is signed or not, and the method of policy deployment that was used.

- &lt;OS Volume&gt;\\Windows\\System32\\CodeIntegrity\\CiPolicies\Active\\*\{PolicyId GUID\}*.cip
- &lt;EFI System Partition&gt;\\Microsoft\\Boot\\CiPolicies\Active\\*\{PolicyId GUID\}*.cip

The *\{PolicyId GUID\}* value is unique by policy and defined in the policy XML with the &lt;PolicyId&gt; element.

For **single policy format App Control policies**, in addition to the two preceding locations, also look for a file called SiPolicy.p7b in the following locations:

- &lt;EFI System Partition&gt;\\Microsoft\\Boot\\SiPolicy.p7b
- &lt;OS Volume&gt;\\Windows\\System32\\CodeIntegrity\\SiPolicy.p7b

> [!NOTE]
> A multiple policy format App Control policy using the single policy format GUID `{A244370E-44C9-4C06-B551-F6016E563076}` might exist under any of the policy file locations.

### File Rule Precedence Order

When the App Control engine evaluates files against the active set of policies on the device, rules are applied in the following order. Once a file encounters a match, App Control stops further processing.

1. Any file matching an explicit deny rule is blocked, even if you create other rules to try to allow it. Deny rules can use any [rule level](../design/select-types-of-rules-to-create.md#app-control-for-business-file-rule-levels). Use the most specific rule level practical when creating deny rules to avoid blocking more than you intend.

2. Any file matching an explicit allow rule runs.

3. Any file that has a [Managed Installer](../design/configure-authorized-apps-deployed-with-a-managed-installer.md) or [Intelligent Security Graph (ISG)](../design/use-appcontrol-with-intelligent-security-graph.md) extended attribute (EA) runs if the policy enables the matching option (managed installer or ISG).

4. Any file that isn't allowed based on the preceding conditions, is checked for reputation using the ISG when that option is enabled in the policy. The file runs if the ISG decides that it's safe and a new ISG EA is written on the file.

5. Any file not allowed by an explicit rule, or based on ISG or managed installer, is blocked implicitly.

## Known issues

### App Control policies in Audit mode might affect performance on a device

When a file is assessed against the current set of App Control policies, the App Control engine sets kernel Extended Attributes (EAs) on the file when it passes the active policies. Later, if the same file runs, App Control checks the EAs and reuses the cached result as long as the policies in effect remain unchanged. This caching mechanism ensures App Control scales even when many policies are active containing large numbers of rules. However, this performance optimization isn't used for policies in audit mode. You might observe a performance difference in some cases between systems with only enforced policies compared to systems with audit policies.

### The Intelligent Security Graph (ISG) option can affect performance when the cloud is checked for many files

The ISG option is an incredibly important capability of App Control that eases the complexity of managing rules for individual files and apps. But, since it relies on Cloud-based artificial intelligence (AI) models, you should avoid relying on the ISG to make decisions about the important apps and files you need to run. Reliance on the ISG isn't recommended for critical workloads, Windows OS code, especially code that runs during boot, or situations where performance is most critical. Whenever possible, you should ensure explicit rules exist in the policy or use managed installers instead of the ISG as a way to reduce your policy management overhead.

When considering your tolerance for performance impacts from ISG, consider also the added performance effects of the [preceding issue affecting performance of audit mode policies](#app-control-policies-in-audit-mode-might-affect-performance-on-a-device). Try to avoid running policies in audit mode that heavily rely on ISG authorization for large numbers of files.

### Boot stop failure (blue screen) occurs if more than 32 policies are active

Until you apply the Windows security update released on or after April 9, 2024, your device is limited to 32 active policies. If the maximum number of policies is exceeded, the device bluescreens referencing ci.dll with a bug check value of 0x0000003b. Consider this maximum policy count limit when planning your App Control policies. Any [Windows inbox policies](inbox-appcontrol-policies.md) that are active on the device also count towards this limit. To remove the maximum policy limit, install the Windows security update released on, or after, April 9, 2024 and then restart the device. Otherwise, reduce the number of policies on the device to remain below 32 policies.

> [!NOTE]
> The policy limit wasn't removed on Windows 11 21H2, and remains limited to 32 policies.

### Audit mode policies can change the behavior for some apps or cause app crashes

Although App Control audit mode is designed to avoid any effect on apps, some features are always on/always enforced with any App Control policy that turns on user mode code integrity (UMCI) with the option **0 Enabled:UMCI**. Here's a list of known system changes in audit mode:

- Some script hosts might block code or run code with fewer privileges even in audit mode. See [Script enforcement with App Control](../design/script-enforcement.md) for information about individual script host behaviors.
- Option **19 Enabled:Dynamic Code Security** is always enforced if any UMCI policy includes that option on some versions of Windows and Windows Server. See [App Control and .NET](../design/appcontrol-and-dotnet.md#app-control-and-net-dynamic-code-security-hardening).

### .NET native images might generate false positive block events

In some cases, the code integrity logs where App Control for Business errors and warnings are written include error events for native images generated for .NET assemblies. Typically, native image blocks are functionally benign as a blocked native image falls back to its corresponding assembly and .NET regenerates the native image at its next scheduled maintenance window. To prevent that, compile your .NET application into [native code ahead of time](/dotnet/core/deploying/native-aot) feature.

### .NET doesn't load Component Object Model (COM) objects with mismatched GUIDs

COM objects make it easy for different software components to communicate and work together. To be used by another component, COM objects must be registered with the operating system. The registration includes a GUID that is calculated based on the object's code. Loading and activation of the COM object is done using another part of the registration called the type name. Sometimes a mismatch exists between the registered GUID and the actual GUID of the activated COM object's code. Mismatches might come from bugs in the app's COM object registration code or if the COM object's code is changed in a way that affects the GUID. Normally, Windows and .NET are forgiving about this condition and runs the COM object’s code regardless. But allowing COM objects to load where there are GUID mismatches leaves the system vulnerable to attackers who can exploit the GUID confusion to run unintended code.

To increase App Control's protective effectiveness on a system vulnerable to this attack technique, .NET applies an extra validation to check that the registered COM object GUID matches the system calculated one. If a mismatch is found, .NET doesn't load the COM object and a general COM load error is raised. Apps using COM objects with this condition might behave in unexpected ways and must be updated to fix issues with the app's COM object registration code.

Since this behavior only occurs when App Control policy is enforced on user mode code, you can't detect it while in audit mode. There's no logging or other events when a COM object fails to load due to the extra validation check. Repairing or reinstalling the app can resolve the issue temporarily, but an app update is needed to fix the COM registration issue and prevent future instances of the problem.

There are no policy control options to manage .NET's GUID verification check, meaning the check is always performed. If you see COM object failures after an App Control policy is deployed, contact the software developer or the Independent Software Vendor (ISV) who produces the app to request a fix for the issue.

### Signatures using elliptical curve cryptography (ECC) aren't supported

App Control signer-based rules only work with RSA cryptography. ECC algorithms, such as ECDSA, aren't supported. If App Control blocks a file based on ECC signatures, the corresponding 3089 signature information events show VerificationError = 23. You can authorize the files instead by hash or file attribute rules, or using other signer rules if the file is also signed with signatures using RSA.

### MSI installers are treated as user writeable on Windows 10 when allowed by FilePath rule

MSI installer files are always detected as user writeable on Windows 10, and on Windows Server 2022 and earlier. If you need to allow MSI files using FilePath rules, you must set option **18 Disabled:Runtime FilePath Rule Protection** in your App Control policy.

### MSI installers launched directly from the internet are blocked

Installing .msi files directly from the internet to a computer protected by App Control fails.
For example, this command fails:

```cmd
msiexec -i https://download.microsoft.com/download/2/E/3/2E3A1E42-8F50-4396-9E7E-76209EA4F429/Windows10_Version_1511_ADMX.msi
```

As a workaround, download the MSI file and run it locally:

```cmd
msiexec -i c:\temp\Windows10_Version_1511_ADMX.msi
```

### Slow boot and performance with custom policies

App Control evaluates all processes that run, including inbox Windows processes. You can cause slower boot times, degraded performance, and possibly boot issues if your policies don't build upon the App Control templates or don't trust the Windows signers. For these reasons, you should use the [App Control base templates](../design/example-appcontrol-base-policies.md) whenever possible to create your policies.

### AppId Tagging policy evaluates DLL files that aren't in scope for tagging

When you use AppId Tagging policies, the result is metadata, the "tags", added to the process token of any executable file that passes the policy. You can then use the tags to change the behavior of an app or component that understands AppId tag and looks for a matching tag on a process. For example, you can set a Windows Firewall rule that uses a custom tag to identify processes that should be allowed to connect through the Firewall. AppId Tags only apply to executable files (EXEs) and never apply to other types of code such as Dynamic Link Libraries (DLLs). But when a DLL runs, App Control evaluates the file against your policy unless a rule exists to allow all files of that type. To short circuit policy evaluation for DLLs and further reduce App Control's affect on performance, add the following rule to your AppId Tagging policies:

:::image type="content" source="../images/known-issue-appid-dll-rule.png" alt-text="Allow all dlls in the policy.":::

:::image type="content" source="../images/known-issue-appid-dll-rule-xml.png" alt-text="Allow all dll files in the xml policy.":::
