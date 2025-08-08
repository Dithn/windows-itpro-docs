---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Remote Credential Guard

Remote Credential Guard helps organizations protect credentials over a Remote Desktop connection by redirecting the Kerberos requests back to the device that is requesting the connection. It also provides single sign-on experiences for Remote Desktop sessions.

Administrator credentials are highly privileged and must be protected. When Remote Credential Guard is configured to connect during Remote Desktop sessions, the credential and credential derivatives are never passed over the network to the target device. If the target device is compromised, the credentials aren't exposed.

[!INCLUDE [learn-more](learn-more.md)]

- [Remote Credential Guard](/windows/security/identity-protection/remote-credential-guard)
