---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Smart cards

Organizations can also opt for smart cards, an authentication method that existed before biometric authentication. These tamper-resistant, portable storage devices enhance Windows security by authenticating users, signing code, securing e-mails, and signing in with Windows domain accounts.

Smart cards provide:

- Ease of use in scenarios such as healthcare, where users need to sign in and out quickly without using their hands or when sharing a workstation
- Isolation of security-critical computations that involve authentication, digital signatures, and key exchange from other parts of the computer. These computations are performed on the smart card
- Portability of credentials and other private information between computers at work, home, or on the road

Smart cards can only be used to sign in to domain accounts or Microsoft Entra ID accounts.

When a password is used to sign in to a domain account, Windows uses the Kerberos Version 5 (V5) protocol for authentication. If you use a smart card, the operating system uses Kerberos V5 authentication with X.509 V3 certificates. On Microsoft Entra ID joined devices, a smart card can be used with Microsoft Entra ID certificate-based authentication. Smart cards can't be used with local accounts.

Windows Hello for Business and FIDO2 security keys are modern, two-factor authentication methods for Windows. Customers using virtual smart cards are encouraged to move to Windows Hello for Business or FIDO2. For new Windows installations, we recommend Windows Hello for Business or FIDO2 security keys.

[!INCLUDE [learn-more](learn-more.md)]

- [Smart Card technical reference](/windows/security/identity-protection/smart-cards/smart-card-windows-smart-card-technical-reference)
