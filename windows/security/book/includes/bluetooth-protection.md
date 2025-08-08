---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Bluetooth protection

The number of Bluetooth devices connected to Windows 11 continues to increase. Windows users connect their Bluetooth headsets, mice, keyboards, and other accessories and improve their day-to-day PC experience by enjoying streaming, productivity, and gaming. Windows supports all standard Bluetooth pairing protocols, including classic and LE Secure connections, secure simple pairing, and classic and LE legacy pairing. Windows also implements host-based LE privacy. Windows updates help users stay current with OS and driver security features in accordance with the Bluetooth Special Interest Group (SIG) and Standard Vulnerability Reports, as well as issues beyond those required by the Bluetooth core industry standards. Microsoft strongly recommends that Bluetooth accessories' firmware and software are kept up to date.

IT-managed environments have a number policy settings available via configuration service providers, group policy, and PowerShell. These settings can be managed through device management solutions like Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup>. You can configure Windows to use Bluetooth technology while supporting the security needs of your organization. For example, you can allow input and audio while blocking file transfer, force encryption standards, limit Windows discoverability, or even disable Bluetooth entirely for the most sensitive environments.

[!INCLUDE [learn-more](learn-more.md)]

- [Policy CSP - Bluetooth](/windows/client-management/mdm/policy-csp-bluetooth)
