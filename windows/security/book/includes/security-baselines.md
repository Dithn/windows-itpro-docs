---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Security baselines

Every organization faces security threats. However, different organizations can be concerned with different types of security threats. For example, an e-commerce company might focus on protecting its internet-facing web apps, while a hospital on confidential patient information. The one thing that all organizations have in common is a need to keep their apps and devices secure. These devices must be compliant with the security standards (or security baselines) defined by the organization.

A security baseline is a group of Microsoft-recommended configuration settings that explains their security implications. These settings are based on feedback from Microsoft security engineering teams, product groups, partners, and customers.

[!INCLUDE [learn-more](learn-more.md)]

- [Security baselines](/windows/security/operating-system-security/device-management/windows-security-configuration-framework/windows-security-baselines)

### Security baseline for cloud-based device management solutions

Windows 11 can be configured with Microsoft's security baseline, designed for cloud-based device management solutions like Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup>. These security baselines function similarly to group policy-based ones and can be easily integrated into existing device management tools.

The security baseline includes policies for:

- Microsoft inbox security technologies such as BitLocker, Microsoft Defender SmartScreen, Virtualization-based security, Exploit Guard, Microsoft Defender Antivirus, and Windows Firewall
- Restricting remote access to devices
- Setting credential requirements for passwords and PINs
- Restricting the use of legacy technology

[!INCLUDE [learn-more](learn-more.md)]

- [Intune security baseline overview](/mem/intune/protect/security-baselines)
- [List of the settings in the Windows security baseline in Intune](/mem/intune/protect/security-baseline-settings-mdm-all)
