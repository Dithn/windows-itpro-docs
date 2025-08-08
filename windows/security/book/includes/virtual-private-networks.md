---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Virtual private networks (VPN)

Organizations have long relied on Windows to provide reliable, secured, and manageable virtual private network (VPN) solutions. The Windows VPN client platform includes built-in VPN
protocols, configuration support, a common VPN user interface, and programming support for custom VPN protocols. VPN apps are available in the Microsoft Store for both enterprise and
consumer VPNs, including apps for the most popular enterprise VPN gateways.

In Windows 11, we've integrated the most commonly used VPN controls right into the Windows 11 Quick Actions pane. From the Quick Actions pane, users can verify the status of their VPN, start and stop the connection, and easily open Settings for more controls.

The Windows VPN platform connects to Microsoft Entra ID<sup>[\[4\]](../conclusion.md#footnote4)</sup> and Conditional Access for single sign-on, including multifactor authentication (MFA) through Microsoft Entra ID. The VPN platform also supports classic domain-joined authentication. It's supported by Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup> and other device management solutions. The flexible VPN profile supports both built-in protocols and custom protocols. It can configure multiple authentication methods and can be automatically started as needed or manually started by the end user. It also supports split-tunnel VPN and exclusive VPN with exceptions for trusted external sites.

With Universal Windows Platform (UWP) VPN apps, end users never get stuck on an old version of their VPN client. VPN apps from the store will be automatically updated as needed. Naturally, the updates are in the control of your IT admins.

The Windows VPN platform is tuned and hardened for cloud-based VPN providers like Azure VPN. Features like Microsoft Entra ID authentication, Windows user interface integration, plumbing IKE traffic selectors, and server support are all built into the Windows VPN platform. The integration into the Windows VPN platform leads to a simpler IT admin experience. User authentication is more consistent, and users can easily find and control their VPN.

[!INCLUDE [learn-more](learn-more.md)]

- [Windows VPN technical guide](/windows/security/operating-system-security/network-security/vpn/vpn-guide)
