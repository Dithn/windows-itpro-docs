---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## :::image type="icon" source="../images/microsoft-entra-id.svg" border="false"::: Microsoft Entra ID

Microsoft Entra ID is a comprehensive cloud-based identity management solution that helps enable secure access to applications, networks, and other resources and guard against threats. Microsoft Entra ID can also be used with Windows Autopilot for zero-touch provisioning of devices preconfigured with corporate security policies.

Organizations can deploy Microsoft Entra ID joined devices to enable access to both cloud and on-premises apps and resources. Access to resources can be controlled based on the Microsoft Entra ID account and Conditional Access policies applied to the device. For the most seamless and delightful end to end single sign-on (SSO) experience, we recommend users configure Windows Hello for Business during the out of box experience for easy passwordless sign-in to Entra ID .

:::row:::
    :::column:::
        For users wanting to connect to Microsoft Entra on their personal devices, they can do so by adding their work or school account to Windows. This action registers the user's personal device with Microsoft Entra ID, allowing IT admins to support users in bring your own device (BYOD) scenarios. Credentials are authenticated and bound to the joined device, and can't be copied to another device without explicit reverification.
    :::column-end:::
    :::column:::
:::image type="content" source="../images/device-registration.png" alt-text="Screenshot of the Entra account registration page." border="false" lightbox="../images/device-registration.png":::
    :::column-end:::
:::row-end:::

To provide more security and control for IT and a seamless experience for users, Microsoft Entra ID works with apps and services, including on-premises software and thousands of software-as-a-service (SaaS) applications. Microsoft Entra ID protections include single sign-on, multifactor authentication, conditional access policies, identity protection, identity governance, and privileged identity management.

Windows 11 works with Microsoft Entra ID to provide secure access, identity management, and single sign-on to apps and services from anywhere. Windows has built-in settings to add work or school accounts by syncing the device configuration to an Active Directory domain or Microsoft Entra ID tenant.

:::image type="content" source="../images/access-work-or-school.png" alt-text="Screenshot of the add work or school account in Settings." border="false":::

When a device is Microsoft Entra ID joined and managed with Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup>, it receives the following security benefits:

- Default managed user and device settings and policies
- Single sign-in to all Microsoft Online Services
- Full suite of authentication management capabilities using Windows Hello for Business
- Single sign-on (SSO) to enterprise and SaaS applications
- No use of consumer Microsoft account identity

Organizations and users can join or register their Windows devices with Microsoft Entra ID to get a seamless experience to both native and web applications. In addition, users can set up Windows Hello for Business or FIDO2 security keys with Microsoft Entra ID and benefit from greater security with passwordless authentication.

In combination with Microsoft Intune, Microsoft Entra ID offers powerful security control through Conditional Access to restrict access to organizational resources to healthy and compliant devices. Note that Microsoft Entra ID is only supported on Windows Pro and Enterprise editions.

Every Windows device has a built-in local administrator account that must be secured and protected to mitigate any Pass-the-Hash (PtH) and lateral traversal attacks. Many customers have been using our standalone, on-premises Windows Local Administrator Password Solution (LAPS) to manage their domain-joined Windows machines. We heard from many customers that LAPS support was needed as they modernized their Windows environment to join directly to Microsoft Entra ID.

[!INCLUDE [learn-more](learn-more.md)]

- [Microsoft Entra ID documentation][LINK-1]
- [Microsoft Entra plans and pricing][LINK-2]

### Microsoft Entra Private Access

Microsoft Entra Private Access provides organizations the ability to manage and give users access to private or internal fully qualified domain names (FQDNs) and IP addresses. With Private Access, you can modernize how your organization's users access private apps and resources. Remote workers don't need to use a VPN to access these resources if they have the Global Secure Access Client installed. The client quietly and seamlessly connects them to the resources they need.

[!INCLUDE [learn-more](learn-more.md)]

- [Microsoft Entra Private Access][LINK-4]

### Microsoft Entra Internet Access

Microsoft Entra Internet Access provides an identity-centric Secure Web Gateway (SWG) solution for Software as a Service (SaaS) applications and other Internet traffic. It protects users, devices, and data from the Internet's wide threat landscape with best-in-class security controls and visibility through Traffic Logs.

> [!NOTE]
> Both Microsoft Entra Private Access and Microsoft Entra Internet Access requires Microsoft Entra ID and Microsoft Entra Joined devices for deployment. The two solutions use the Global Secure Access client for Windows, which secures and controls the features.

[!INCLUDE [learn-more](learn-more.md)]

- [Microsoft Entra Internet Access][LINK-3]
- [Global Secure Access client for Windows][LINK-6]
- [Microsoft's Security Service Edge Solution Deployment Guide for Microsoft Entra Internet Access Proof of Concept][LINK-5]

### Enterprise State Roaming

Available to any organization with a Microsoft Entra ID Premium<sup>[\[4\]](../conclusion.md#footnote4)</sup> license, Enterprise State Roaming provides users with a unified Windows Settings experience across their Windows devices and reduces the time needed for configuring a new device.

[!INCLUDE [learn-more](learn-more.md)]

- [Enterprise State Roaming in Microsoft Entra ID][LINK-7]

[LINK-1]: /entra
[LINK-2]: https://www.microsoft.com/security/business/microsoft-entra-pricing
[LINK-3]: /entra/global-secure-access/concept-internet-access
[LINK-4]: /entra/global-secure-access/concept-private-access
[LINK-5]: /entra/architecture/sse-deployment-guide-internet-access
[LINK-6]: /entra/global-secure-access/how-to-install-windows-client
[LINK-7]: /entra/identity/devices/enterprise-state-roaming-enable
