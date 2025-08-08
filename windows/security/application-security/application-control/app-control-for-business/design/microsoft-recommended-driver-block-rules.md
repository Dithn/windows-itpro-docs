---
title: Microsoft recommended driver block rules
description: View a list of recommended block rules to block vulnerable third-party drivers discovered by Microsoft and the security research community.
ms.localizationpriority: medium
ms.collection:
- tier3
- must-keep
ms.date: 09/11/2024
ms.topic: how-to
---

# Microsoft recommended driver block rules

[!INCLUDE [Feature availability note](../includes/feature-availability-note.md)]

Microsoft has strict requirements for code running in kernel. So, malicious actors are turning to exploit vulnerabilities in legitimate and signed kernel drivers to run malware in kernel. One of the many strengths of the Windows platform is our strong collaboration with independent hardware vendors (IHVs) and OEMs. Microsoft works closely with our IHVs and security community to ensure the highest level of driver security for our customers. When vulnerabilities in drivers are found, we work with our partners to ensure they're quickly patched and rolled out to the ecosystem. The vulnerable driver blocklist is designed to help harden systems against non-Microsoft-developed drivers across the Windows ecosystem with any of the following attributes:

- Known security vulnerabilities that can be exploited by attackers to elevate privileges in the Windows kernel
- Malicious behaviors (malware) or certificates used to sign malware
- Behaviors that aren't malicious but circumvent the Windows Security Model and can be exploited by attackers to elevate privileges in the Windows kernel

Drivers can be submitted to Microsoft for security analysis at the [Microsoft Security Intelligence Driver Submission page](https://www.microsoft.com/wdsi/driversubmission). For more information about driver submission, see [Improve kernel security with the new Microsoft Vulnerable and Malicious Driver Reporting Center](https://www.microsoft.com/security/blog/2021/12/08/improve-kernel-security-with-the-new-microsoft-vulnerable-and-malicious-driver-reporting-center/). To report an issue or request a change to the blocklist, including updating a block rule once a driver has been fixed, visit the [Microsoft Security Intelligence portal](https://www.microsoft.com/wdsi).

> [!NOTE]
> Blocking drivers can cause devices or software to malfunction, and in rare cases, lead to blue screen. The vulnerable driver blocklist is not guaranteed to block every driver found to have vulnerabilities. Microsoft attempts to balance the security risks from vulnerable drivers with the potential impact on compatibility and reliability to produce the blocklist. As always, Microsoft recommends using an explicit allow list approach to security wherever possible.

## Microsoft vulnerable driver blocklist

<!-- MAXADO-6286432 -->

With Windows 11 2022 update, the vulnerable driver blocklist  is enabled by default for all devices, and can be turned on or off via the [Windows Security](https://support.microsoft.com/windows/device-protection-in-windows-security-afa11526-de57-b1c5-599f-3a4c6a61c5e2) app. Except on Windows Server 2016, the vulnerable driver blocklist is also enforced when either memory integrity (also known as hypervisor-protected code integrity or HVCI), Smart App Control, or S mode is active. Users can opt in to HVCI using the [Windows Security](https://support.microsoft.com/windows/device-protection-in-windows-security-afa11526-de57-b1c5-599f-3a4c6a61c5e2) app, and HVCI is on by-default for most new Windows 11 devices.

> [!NOTE]
>
> - **Windows Security** is updated separately from the OS and ships out of box. The version with the vulnerable driver blocklist toggle is in the final validation ring and will ship to all customers very soon. Initially, you will be able to view the configuration state only and the toggle will appear grayed out. The ability to turn the toggle on or off will come with a future Windows update.
>
> - For Windows Insiders, the option to turn Microsoft's vulnerable driver blocklist on or off using **Windows Security** settings is grayed out when HVCI, Smart App Control, or S mode is enabled. You must disable HVCI or Smart App Control, or switch the device out of S mode, and restart the device before you can turn off the Microsoft vulnerable driver blocklist.

The blocklist is updated with each new major release of Windows, typically 1-2 times per year. The most current blocklist is now also available for Windows 10 20H2 and Windows 11 21H2 users as an optional update from Windows Update. Microsoft will occasionally publish future updates through regular Windows servicing.

Customers who always want the most up-to-date driver blocklist can also use App Control for Business to apply the latest recommended driver blocklist. For your convenience, we provide a download of the most up-to-date vulnerable driver blocklist along with instructions to apply it on your computer at the end of this article.

## Blocking vulnerable drivers using App Control

Microsoft recommends enabling [HVCI](../../../../hardware-security/enable-virtualization-based-protection-of-code-integrity.md) or S mode to protect your devices against security threats. If this setting isn't possible, Microsoft recommends blocking [this list of drivers](#vulnerable-driver-blocklist-xml) within your existing App Control for Business policy. Blocking kernel drivers without sufficient testing can cause devices or software to malfunction, and in rare cases, blue screen. It's recommended to first validate this policy in [audit mode](../deployment/audit-appcontrol-policies.md) and review the audit block events.

> [!IMPORTANT]
> Microsoft also recommends enabling Attack Surface Reduction (ASR) rule [**Block abuse of exploited vulnerable signed drivers**](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference#block-abuse-of-exploited-vulnerable-signed-drivers) to prevent an application from writing a vulnerable signed driver to disk. The ASR rule doesn't block a driver already existing on the system from loading, however enabling **Microsoft vulnerable driver blocklist** or applying this App Control policy will prevent the existing driver from loading.

## Steps to download and apply the vulnerable driver blocklist binary

If you prefer to apply the vulnerable driver blocklist, follow these steps:

1. Download the [App Control policy refresh tool](https://aka.ms/refreshpolicy)
2. Download and extract the [vulnerable driver blocklist binaries](https://aka.ms/VulnerableDriverBlockList)
3. Select either the audit only version or the enforced version and rename the file to SiPolicy.p7b
4. Copy SiPolicy.p7b to %windir%\system32\CodeIntegrity
5. Run the App Control policy refresh tool you downloaded in Step 1 above to activate and refresh all App Control policies on your computer

To check that the policy was successfully applied on your computer:

1. Open Event Viewer
2. Browse to **Applications and Services Logs - Microsoft - Windows - CodeIntegrity - Operational**
3. Select **Filter Current Log...**
4. Replace "&lt;All Event IDs&gt;" with "3099" and select OK.
5. Look for a 3099 event where the PolicyNameBuffer and PolicyIdBuffer match the Name and Id PolicyInfo settings found at the bottom of the blocklist App Control Policy XML in this article. NOTE: Your computer may have more than one 3099 event if other App Control policies are also present.

> [!NOTE]
> If any vulnerable drivers are already running that would be blocked by the policy, you must reboot your computer for those drivers to be blocked. Running processes aren't shutdown when activating a new App Control policy without reboot.

## Vulnerable driver blocklist XML

The recommended blocklist xml policy file can be downloaded from the [Microsoft Download Center](https://aka.ms/VulnerableDriverBlockList).

This policy contains **Allow All** rules. If your version of Windows supports App Control multiple policies, we recommend deploying this policy alongside any existing App Control policies. If you do plan to merge this policy with another policy, you may need to remove the **Allow All** rules before merging it if the other policy applies an explicit allow list. For more information, see [Create an App Control Deny Policy](create-appcontrol-deny-policy.md#guidance-on-creating-app-control-deny-policies).

> [!NOTE]
> To use this policy with Windows Server 2016, you must convert the policy XML on a device running a newer operating system.

## More information

- [Merge App Control for Business policies](../deployment/merge-appcontrol-policies.md)
