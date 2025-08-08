---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Local Security Authority (LSA) protection

Windows has several critical processes to verify a user's identity. Verification processes include Local Security Authority (LSA), which is responsible for authenticating users, and verifying Windows sign-ins. LSA handles tokens and credentials that are used for single sign-on to a Microsoft account and Entra ID account.

By loading only trusted, signed code, LSA provides significant protection against credential theft. LSA protection supports configuration using group policy and other device management solutions.

[!INCLUDE [new-24h2](new-24h2.md)]

To help keep these credentials safe, LSA protection is enabled by default on all devices (MSA, Microsoft Entra joined, hybrid, and local). For new installs, it's enabled immediately. For upgrades, it's enabled after rebooting after an evaluation period of five days.

Users have the ability to manage the LSA protection state in the Windows Security application under **Device Security** > **Core Isolation** > **Local Security Authority protection**.

To ensure a seamless transition and enhanced security for all users, the enterprise policy for LSA protection takes precedence over enablement on upgrade.

[!INCLUDE [learn-more](learn-more.md)]

- [Configuring additional LSA protection](/windows-server/security/credentials-protection-and-management/configuring-additional-lsa-protection)