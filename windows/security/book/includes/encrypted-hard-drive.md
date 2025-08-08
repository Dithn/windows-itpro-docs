---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Encrypted hard drive

Encrypted hard drives are a class of hard drives that are self-encrypted at the hardware level. They allow for full-disk hardware encryption and are transparent to the user. These drives combine the security and management benefits provided by BitLocker, with the power of self-encrypting drives.

By offloading the cryptographic operations to hardware, encrypted hard drives increase BitLocker performance and reduce CPU usage and power consumption. Because encrypted hard drives encrypt data quickly, BitLocker deployment can be expanded across enterprise devices with little to no impact on productivity.

Encrypted hard drives enable:

- Smooth performance: encryption hardware integrated into the drive controller allows the drive to operate at full data rate without performance degradation
- Strong security based in hardware: encryption is always-on, and the keys for encryption never leave the hard drive. The drive authenticates the user independently from the operating system before it unlocks
- Ease of use: encryption is transparent to the user, and the user doesn't need to enable it. Encrypted hard drives are easily erased using an onboard encryption key. There's no need to re-encrypt data on the drive
- Lower cost of ownership: there's no need for new infrastructure to manage encryption keys since BitLocker uses your existing infrastructure to store recovery information. Your device operates more efficiently because processor cycles don't need to be used for the encryption process

[!INCLUDE [learn-more](learn-more.md)]

- [Encrypted hard drive](/windows/security/operating-system-security/data-protection/encrypted-hard-drive)
