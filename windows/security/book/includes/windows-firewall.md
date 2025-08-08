---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Windows Firewall

Windows Firewall is an important part of a layered security model. It provides host-based, two-way network traffic
filtering, blocking unauthorized traffic flowing into or out of the local device based on the types of networks the device is connected to.

Windows Firewall offers the following benefits:

- Reduces the risk of network security threats: Windows Firewall reduces the attack surface of a device with rules that restrict or allow traffic by many properties, such as IP addresses, ports, or program paths. This functionality increases manageability and decreases the likelihood of a successful attack
- Safeguards sensitive data and intellectual property: By integrating with Internet Protocol Security (IPSec), Windows Firewall provides a simple way to enforce authenticated, end-to-end network communications. It provides scalable, tiered access to trusted network resources, helping to enforce integrity of the data, and optionally helping to protect the confidentiality of the data
- Extends the value of existing investments: Because Windows Firewall is a host-based firewall that is included with the operating system, there's no extra hardware or software required. Windows Firewall is also designed to complement existing non-Microsoft network security solutions through a documented application programming interface (API)

Windows 11 makes the Windows Firewall easier to analyze and debug. IPSec behavior is integrated with Packet Monitor, an in-box, cross-component network diagnostic tool for Windows. Additionally, the Windows Firewall event logs are enhanced to ensure an audit can identify the specific filter that was responsible for any given event. This enables analysis of firewall behavior and rich packet capture without relying on third-party tools.

Admins can configure more settings through the Firewall and Firewall Rule policy templates in the Endpoint Security node in Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup>, using the platform support from the Firewall configuration service provider (CSP) and applying these settings to Windows endpoints.

[!INCLUDE [new-24h2](new-24h2.md)]

The Firewall Configuration Service Provider (CSP) in Windows now enforces an all-or-nothing approach to applying firewall rules within each atomic block. Previously, if the CSP encountered an issue with any rule in a block, it would not only stop processing that rule but also cease processing subsequent rules, potentially leaving a security gap with partially deployed rule blocks. Now, if any rule in the block cannot be successfully applied, the CSP stops processing subsequent rules and roll back all rules from that atomic block, eliminating the ambiguity of partially deployed rule blocks.

[!INCLUDE [learn-more](learn-more.md)]

- [Windows Firewall overview](/windows/security/operating-system-security/network-security/windows-firewall)
- [Firewall CSP](/windows/client-management/mdm/firewall-csp)
