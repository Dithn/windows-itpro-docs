---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## :::image type="icon" source="../images/microsoft-intune.svg" border="false"::: Microsoft Intune

Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup> is a comprehensive cloud-native endpoint management solution that helps secure, deploy, and manage users, apps, and devices. Intune brings together technologies like Microsoft Configuration Manager and Windows Autopilot to simplify provisioning, configuration management, and software updates across the organization.

Intune works with Microsoft Entra ID to manage security features and processes, including multifactor authentication and conditional access.

Organizations can cut costs while securing and managing remote devices through the cloud in compliance with company policies<sup>[\[11\]](../conclusion.md#footnote11)</sup>. For example, organizations can save time and money by provisioning preconfigured devices to remote employees using Windows Autopilot.

Windows 11 enables IT professionals to move to the cloud while consistently enforcing security policies. Windows 11 provides expanded support for group policy administrative templates (ADMX-backed policies) in cloud-native device management solutions like Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup>, enabling IT professionals to easily apply the same security policies to both on-premises and remote devices.

Customers have asked for App Control for Business (previously called *Windows Defender Application Control*) to support manage installer for a long time. Now it's possible to enable allowlisting of Win32 apps to proactively reduce the number of malware infections.

[!INCLUDE [learn-more](learn-more.md)]

- [What is Microsoft Intune](/mem/intune/fundamentals/what-is-intune)

### Windows enrollment attestation

When a device enrolls into device management, the administrator expects it to receive the appropriate policies to secure and manage the PC. However, in some cases, malicious actors can remove enrollment certificates and use them on unmanaged PCs, making them appear enrolled but without the intended security and management policies.

With Windows enrollment attestation, Microsoft Entra and Microsoft Intune certificates are bound to a device using the Trusted Platform Module (TPM). This ensures that the certificates can't be transferred from one device to another, maintaining the integrity of the enrollment process.

[!INCLUDE [learn-more](learn-more.md)]

- [Windows enrollment attestation](/mem/intune/enrollment/windows-enrollment-attestation)

### Microsoft Cloud PKI

Microsoft Cloud PKI is a cloud-based service included in the Microsoft Intune Suite<sup>[\[4\]](../conclusion.md#footnote4)</sup> that simplifies and automates the management of a Public Key Infrastructure (PKI) for organizations. It eliminates the need for on-premises servers, hardware, and connectors, making it easier to set up and manage a PKI compared to, for instance, Microsoft Active Directory Certificate Services (AD CS) combined with the Certificate Connector for Microsoft Intune.

Key features include:

- Certificate lifecycle management: automates the lifecycle of certificates, including issuance, renewal, and revocation, for all devices managed by Intune
- Multi-platform support: supports certificate management for Windows, iOS/iPadOS, macOS, and Android devices
- Enhanced security: enables certificate-based authentication for Wi-Fi, VPN, and other scenarios, improving security over traditional password-based methods. All certificate requests leverage Simple Certificate Enrollment Protocol (SCEP), making sure that the private key never leaves the requesting client
- Simplified management: provides easy management of certification authorities (CAs), registration authorities (RAs), certificate revocation lists (CRLs), monitoring, and reporting

With Microsoft Cloud PKI, organizations can accelerate their digital transformation and achieve a fully managed cloud PKI service with minimal effort.

[!INCLUDE [learn-more](learn-more.md)]

- [Overview of Microsoft Cloud PKI for Microsoft Intune](/mem/intune/protect/microsoft-cloud-pki-overview)

### Endpoint Privilege Management (EPM)

Intune Endpoint Privilege Management supports organizations' Zero Trust journeys by helping them achieve a broad user base running with least privilege, while still permitting users to run elevated tasks allowed by the organization to remain productive.

[!INCLUDE [learn-more](learn-more.md)]

- [Endpoint Privilege Management](/mem/intune/protect/epm-overview?formCode=MG0AV3)

### Mobile application management (MAM)

With Intune, organizations can also extend MAM App Config, MAM App Protection, and App Protection Conditional Access capabilities to Windows. This enables people to access protected organizational content without having the device managed by IT. The first application to support MAM for Windows is Microsoft Edge.

[!INCLUDE [learn-more](learn-more.md)]

- [Data protection for Windows MAM](/mem/intune/apps/protect-mam-windows?formCode=MG0AV3)
