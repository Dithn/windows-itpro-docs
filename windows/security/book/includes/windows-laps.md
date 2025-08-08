---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Windows Local Administrator Password Solution (LAPS)

Windows Local Administrator Password Solution (LAPS) is a feature that automatically manages and backs up the password of a local administrator account on Microsoft Entra joined and Active Directory-joined devices. It helps enhance security by regularly rotating and managing local administrator account passwords, protecting against pass-the-hash and lateral-traversal attacks.

Windows LAPS can be configured via group policy or with a device management solution like Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup>.

[!INCLUDE [new-24h2](new-24h2.md)]

Several enhancements have been made to improve manageability and security. Administrators can now configure LAPS to automatically create managed local accounts, integrating with existing policies to enhance security and efficiency. Policy settings have been updated to generate more readable passwords by ignoring certain characters and to support the generation of readable passphrases, with options to choose from three separate word source list and control passphrase length. Additionally, LAPS can detect when a computer rolls back to a previous image, ensuring password consistency between the computer and Active Directory.

[!INCLUDE [learn-more](learn-more.md)]

- [Windows LAPS overview](/windows-server/identity/laps/laps-overview)
