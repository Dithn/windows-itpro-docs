---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Token protection (preview)

Token protection attempts to reduce attacks using Microsoft Entra ID token theft. Token protection makes tokens usable only from their intended device by cryptographically binding a token with a device secret. When using the token, both the token and proof of the device secret must be provided. Conditional Access policies<sup>[\[4\]](../conclusion.md#footnote4)</sup> can be configured to require token protection when using sign-in tokens for specific services.

[!INCLUDE [learn-more](learn-more.md)]

- [Token protection in Entra ID Conditional Access](/azure/active-directory/conditional-access/concept-token-protection)

### Sign-in session token protection policy

This feature allows applications and services to cryptographically bind security tokens to the device, restricting attackers' ability to impersonate users on a different device if tokens are stolen.
