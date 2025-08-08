---
title: Application Control for Windows
description: Application Control restricts which applications users are allowed to run and the code that runs in the system core.
ms.localizationpriority: medium
ms.collection:
- tier3
ms.date: 03/09/2025
ms.topic: overview
---

# Application Control for Windows

[!INCLUDE [Feature availability note](includes/feature-availability-note.md)]

Your organization's data is one of its most valuable assets... and adversaries want it. No matter what security controls you apply over your data, there are no controls to fully protect your most vulnerable target: the trusted user sitting at the keyboard. When a user runs a process, that process shares the same access to your data that the user has. So your sensitive information is easily transmitted, modified, deleted, or encrypted when a user, intentionally or not, runs malicious software. And with thousands of new malicious files created every day, relying solely on traditional methods like antivirus (AV) solutions gives you an inadequate defense against new attacks.

Application control changes Windows from a place where all code runs unless your AV solution confidently predicts it's bad, to one where code runs only if your policy says so. The cyber threats you face change rapidly, and your defenses need to change too. Government and security organizations, like the Australian Signals Directorate, frequently cite application control as one of the most effective ways to address the threat of executable file-based malware (.exe, .dll, etc.). It works alongside your AV solution to help mitigate security threats by restricting the apps that users can run and even what code runs in the System Core (kernel).

> [!IMPORTANT]
> Although application control can significantly harden your computers against malicious code, it's not a replacement for antivirus. You should continue to maintain an active antivirus solution alongside App Control for a well-rounded enterprise security portfolio.

Although we call it application control, the code running on your system isn't always an app. Application control extends beyond apps to also cover scripts and Microsoft installers (MSI), command-line batch files, and even interactive sessions of Windows PowerShell, which run in [Constrained Language Mode](/powershell/module/microsoft.powershell.core/about/about_language_modes).

Windows includes two application control technologies you can use depending on your organization's specific scenarios and requirements:

- **App Control for Business (app control)**; and
- **AppLocker**

## App Control and Smart App Control

Starting in Windows 11 version 22H2, [Smart App Control](https://support.microsoft.com/topic/what-is-smart-app-control-285ea03d-fa88-4d56-882e-6698afdb7003) brings robust application control to consumers and to some small businesses with simpler app portfolios. Smart App Control ensures only signed code runs or code predicted to be safe by our intelligent cloud-powered security service. When code is unsigned and the service is unable to predict with confidence that it's safe to run, then we block it. Over time, the code's reputation might change as the service processes new signals it receives. Meanwhile, code determined to be unsafe is always blocked.

While Smart App Control is designed for consumers, we believe it's the ideal starting point for most organizations. And since we built it entirely upon App Control for Business, you can create a policy with the same security and compatibility as Smart App Control that also trusts the line-of-business (LOB) apps your organization needs. The service Smart App Control uses to predict what code is safe to run is also available in App Control for Business and called the Intelligent Security Graph (ISG).

Smart App Control starts in evaluation mode and switches off within 48 hours for enterprise managed devices unless the user turns it on first. If you want to proactively turn off Smart App Control across your organization's endpoints, set the **VerifiedAndReputablePolicyState** (DWORD) registry value under `HKLM\SYSTEM\CurrentControlSet\Control\CI\Policy` as shown in the following table. After you change the registry value, you must run [CiTool.exe -r](operations/citool-commands.md#refresh-the-app-control-policies-on-the-system) for the change to take effect.

| Value | Description |
|-------|-------------|
| 0     | Off         |
| 1     | Enforce     |
| 2     | Evaluation  |

> [!IMPORTANT]
> Once you turn Smart App Control off, it can't be turned on without resetting or reinstalling Windows.

The App Control policy used for Smart App Control comes bundled with the [App Control Wizard](design/appcontrol-wizard.md) policy authoring tool and is also found as an [example policy](design/example-appcontrol-base-policies.md) at *%windir%/schemas/CodeIntegrity/ExamplePolicies/SmartAppControl.xml*. To use this example policy as a starting point for your own policy, see [Use the Smart App Control Policy to build your own base policy](design/create-appcontrol-policy-for-lightly-managed-devices.md#use-the-smart-app-control-policy-to-build-your-starter-policy). When using the Smart App Control example policy as the basis for your own custom policy, you must remove the option **Enabled:Conditional Windows Lockdown Policy** so it's ready for use as an App Control for Business policy.

[!INCLUDE [windows-defender-application-control-wdac](../../../../../includes/licensing/windows-defender-application-control-wdac.md)]

## What you should read next

- To learn more about the two application control technologies available in Windows, read [App Control for Business and AppLocker Overview](./appcontrol-and-applocker-overview.md).

- To jump right in and get started creating policies, go revisit Smart App Control and [Use the Smart App Control policy to build your own starter policy](design/create-appcontrol-policy-for-lightly-managed-devices.md).
