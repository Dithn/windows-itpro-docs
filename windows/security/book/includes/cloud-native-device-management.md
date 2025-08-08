---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Cloud-native device management

Microsoft recommends cloud-based device management so that IT professionals can manage company security policies and business applications without compromising user privacy on corporate or employee-owned devices. With cloud-native device management solutions like Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup>, IT can manage Windows 11 using industry standard protocols. To simplify setup for users, management features are built directly into Windows, eliminating the need for a separate device management client.

Windows 11 built-in management features include:

- The enrollment client, which enrolls and configures the device to securely communicate with the enterprise device management server
- The management client, which periodically synchronizes with the management server to check for updates and apply the latest policies set by IT

[!INCLUDE [learn-more](learn-more.md)]

- [Mobile device management overview](/windows/client-management/mdm-overview)

### Remote wipe

When a device is lost or stolen, IT administrators might want to remotely wipe data stored in memory and hard disks. A helpdesk agent might also want to reset devices to fix issues encountered by remote workers. A remote wipe can also be used to prepare a previously used device for a new user.

Windows 11 supports the Remote Wipe configuration service provider (CSP) so that device management solutions can remotely initiate any of the following operations:

- Reset the device and remove user accounts and data
- Reset the device and clean the drive
- Reset the device but persist user accounts and data

[!INCLUDE [learn-more](learn-more.md)]

- [Remote wipe CSP](/windows/client-management/mdm/remotewipe-csp)
