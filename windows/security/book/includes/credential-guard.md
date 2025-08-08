---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Credential Guard

:::row:::
    :::column:::
        Credential Guard uses hardware-backed, Virtualization-based security (VBS) to protect against credential theft. With Credential Guard, the Local Security Authority (LSA) stores and protects Active Directory (AD) secrets in an isolated environment that isn't accessible to the rest of the operating system. LSA uses remote procedure calls to communicate with the isolated LSA process.

By protecting the LSA process with Virtualization-based security, Credential Guard shields systems from user credential theft attack techniques like Pass-the-Hash or Pass-the-Ticket. It also helps prevent malware from accessing system secrets even if the process is running with admin privileges.
    :::column-end:::
    :::column:::
:::image type="content" source="../images/credential-guard-architecture.png" alt-text="Diagram of the Credential Guard's architecture."  lightbox="../images/credential-guard-architecture.png" border="false":::
    :::column-end:::
:::row-end:::

[!INCLUDE [new-24h2](new-24h2.md)]

Credential Guard protections are expanded to optionally include machine account passwords for Active Directory-joined devices. Administrators can enable audit mode or enforcement of this capability using Credential Guard policy settings.

[!INCLUDE [learn-more](learn-more.md)]

- [Protect derived domain credentials with Credential Guard](/windows/security/identity-protection/credential-guard)
