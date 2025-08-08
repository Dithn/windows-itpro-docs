---
title: Policy creation for common App Control usage scenarios
description: Develop a plan for deploying App Control for Business in your organization based on these common scenarios.
ms.localizationpriority: medium
ms.date: 01/31/2025
ms.topic: install-set-up-deploy
---

# App Control for Business deployment in different scenarios: types of devices

[!INCLUDE [Feature availability note](../includes/feature-availability-note.md)]

Whenever possible, App Control for Business (app control) should be enabled when setting up a device for the first time and before installing any apps. This ensures the system is in a "clean" state when App Control starts, and is especially important for apps allowed because they were installed by a managed installer or because the Intelligent Security Graph (ISG) determined that the app was safe to run. 

Typically, deployment of App Control for Business happens best in phases, rather than being a feature that you simply "turn on." The choice and sequence of phases depends on the way various computers and other devices are used in your organization, and to what degree IT manages those devices. The following table can help you begin to develop a plan for deploying App Control in your organization. It's common for organizations to have device use cases across each of the categories described.

## Common use cases

|  Use case | How App Control relates to this use case  |
|------------------------------------|------------------------------------------------------|
| **Block undesirable apps**: Few companies manage all apps centrally, needing a long discovery period before they can even begin to decide what to allow. <BR> Instead, the IT department's focus shifts to block a set of apps they consider problems, while they build their inventory of apps. | Using App Control, deploy a blocklist-only policy alongside an audit allowlist policy to gather information about the apps and processes running on your devices. |
| **Lightly managed devices**: Company-owned, but users are free to install software.<br>Devices are required to run specific apps, like the organization's antivirus solution or its helpdesk client management tools. | App Control for Business can be used to help protect the kernel, and to let users run apps that are signed, are installed by the company's app deployment solution like Intune, were installed to locations where only an admin can write files, and any app with good reputation. |
| **Fully managed devices**: Allowed software is restricted by your IT department.<br>Users can request for more software, or install from a list of applications provided by the IT department.<br>Examples: locked-down, company-owned desktops and laptops. | An initial baseline App Control for Business policy can be established and enforced. Whenever the IT department approves more applications, they may update the App Control policy as part of their app packaging and deployment processes. Alternatively, they may create and sign app catalog files that are then distributed as a dependency of the app. |
| **Fixed-workload devices**: Perform same tasks every day.<br>Lists of approved applications rarely change.<br>Examples: kiosks, point-of-sale systems, call center computers. | App Control for Business can be deployed fully, and deployment and ongoing administration are relatively straightforward.<br>After App Control for Business deployment, only approved applications can run. This rule is because of protections offered by App Control. |
| **Bring Your Own Device**: Employees are allowed to bring their own devices, and also use those devices away from work. | In most cases, App Control for Business doesn't apply. Instead, you can explore other hardening and security features with MDM-based conditional access solutions, such as Microsoft Intune. However, you may choose to deploy an audit-mode policy to these devices or employ a blocklist only policy to prevent specific apps or binaries that are considered malicious or vulnerable by your organization. |
| **"Dirty" systems**: Introducing an app control solution on systems that are already in use is much more challenging than when you apply it to a new device that hasn't installed any apps yet. Sometimes, trade-offs must be made to maintain productivity even if some apps might be unwanted by the organization. | Using a script to apply App Control policies, organizations can create a policy by scanning each device and creating rules for every binary or script file observed. This set of rules is used to supplement the more restrictive Base policy applied to fresh devices, newly configured. This way, any previously installed app keeps working, but all future installs must pass the organizations newly enforced app control rules. |

## An introduction to Lamna Healthcare Company

In the next set of articles, we'll explore policies to handle scenarios like the ones in the table using a fictional company called Lamna Healthcare Company.

Lamna Healthcare Company (Lamna) is a large healthcare provider operating in the United States. Lamna employs thousands of people, from doctors and nurses to accountants, in-house lawyers, and IT technicians. Their device use cases are varied and include single-user workstations for their professional staff, shared kiosks used by doctors and nurses to access patient records, dedicated medical devices such as MRI scanners, and many others. Additionally, Lamna has a relaxed, bring-your-own-device policy for many of their professional staff.

Lamna uses [Microsoft Intune](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) in hybrid mode with both Configuration Manager and Intune. Although they use Microsoft Intune to deploy many applications, Lamna has always had relaxed application usage practices: individual teams and employees have been able to install and use any applications they deem necessary for their role on their own workstations. Lamna also recently started to use [Microsoft Defender for Endpoint](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp) for better endpoint detection and response.

Recently, Lamna experienced a ransomware event that required an expensive recovery process and may have included data exfiltration by the unknown attacker. Part of the attack included installing and running malicious binaries that evaded detection by Lamna's antivirus solution but would have been blocked by an App Control policy. In response, Lamna's executive board has authorized many new security IT responses, including tightening policies for application use and introducing App Control.

## Up next

Now, let's create our initial policy using the [Smart App Control](../appcontrol.md#app-control-and-smart-app-control) "circle of trust" as our starting point.

- [Use the Smart App Control policy to build your starter base policy](./create-appcontrol-policy-for-lightly-managed-devices.md).

Or, if you prefer:

- [Use an App Control policy to block specific apps](./create-appcontrol-deny-policy.md).
