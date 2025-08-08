---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Personal Data Encryption

Personal Data Encryption is a user-authenticated encryption mechanism designed to protect user's content. Personal Data Encryption uses Windows Hello for Business as its modern authentication scheme, with PIN or biometric authentication methods. The encryption keys used by Personal Data Encryption are securely stored within the Windows Hello container. When a user signs in with Windows Hello, the container is unlocked, making the keys available to decrypt the user's content.

The initial release of Personal Data Encryption in Windows 11, version 22H2, introduced a set of public APIs that applications can adopt to safeguard content.

[!INCLUDE [new-24h2](new-24h2.md)]

Personal Data Encryption is further enhanced with *Personal Data Encryption for known folders*, which extends protection to the Windows folders: Documents, Pictures, and Desktop.

:::image type="content" source="../images/pde.png" alt-text="Screenshot of files encrypted with Personal Data Encryption showing a padlock." border="false":::

[!INCLUDE [learn-more](learn-more.md)]

- [Personal Data Encryption](/windows/security/operating-system-security/data-protection/personal-data-encryption)
