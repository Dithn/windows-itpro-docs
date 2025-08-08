---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Device encryption

Device encryption is a Windows feature that simplifies the process of enabling BitLocker encryption on certain devices. It ensures that only the OS drive and fixed drives are encrypted, while external/USB drives remain unencrypted. Additionally, devices with externally accessible ports that allow DMA access are not eligible for device encryption. Unlike standard BitLocker implementation, device encryption is enabled automatically to ensure continuous protection. Once a clean installation of Windows is completed and the out-of-box experience is finished, the device is prepared for first use with encryption already in place.

Organizations have the option to disable device encryption in favor of a full BitLocker implementation. This allows for more granular control over encryption policies and settings, ensuring that the organization's specific security requirements are met.

[!INCLUDE [new-24h2](new-24h2.md)]

The Device encryption prerequisites of DMA and HSTI/Modern Standby are removed. This change makes more devices eligible for both automatic and manual device encryption.

[!INCLUDE [learn-more](learn-more.md)]

- [Device encryption](/windows/security/operating-system-security/data-protection/bitlocker#device-encryption)
