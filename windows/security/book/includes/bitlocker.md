---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## BitLocker

BitLocker is a data protection feature that integrates with the operating system to address the threats of data theft or exposure from lost, stolen, or improperly decommissioned devices. It uses the AES algorithm in XTS or CBC mode with 128-bit or 256-bit key lengths to encrypt data on the volume. During the initial setup, when BitLocker is enabled during OOBE and the user signs into their Microsoft account for the first time, BitLocker automatically saves its recovery password to the Microsoft account for retrieval if needed. Users also have the option to export the recovery password if they manually enable BitLocker. Recovery key content can be saved to cloud storage on OneDrive or Azure<sup>[\[4\]](../conclusion.md#footnote4)</sup>.

For organizations, BitLocker can be managed via group policy or with a device management solution like Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup>. It provides encryption for the OS, fixed data, and removable data drives (BitLocker To Go), using technologies such as Hardware Security Test Interface (HSTI), Modern Standby, UEFI Secure Boot, and TPM.

[!INCLUDE [new-24h2](new-24h2.md)]

The BitLocker preboot recovery screen includes the Microsoft account (MSA) hint, if the recovery password is saved to an MSA. This hint helps the user to understand which MSA account was used to store recovery key information.

[!INCLUDE [learn-more](learn-more.md)]

- [BitLocker overview](/windows/security/operating-system-security/data-protection/bitlocker/index)

### BitLocker To Go

BitLocker To Go refers to BitLocker on removable data drives. BitLocker To Go includes the encryption of USB flash drives, SD cards, and external hard disk drives. Drives can be unlocked using a password, certificate on a smart card, or recovery password.

[!INCLUDE [learn-more](learn-more.md)]

- [BitLocker FAQ](/windows/security/operating-system-security/data-protection/bitlocker/faq)
