---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Certificates

To help safeguard and authenticate information, Windows provides comprehensive support for certificates and certificate management. The built-in certificate management command-line utility (certmgr.exe) or Microsoft Management Console (MMC) snap-in (certmgr.msc) can be used to view and manage certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs). Whenever a certificate is used in Windows, we validate that the leaf certificate and all the certificates in its chain of trust haven't been revoked or compromised. The trusted root and intermediate certificates and publicly revoked certificates on the machine are used as a reference for Public Key Infrastructure (PKI) trust and are updated monthly by the Microsoft Trusted Root program. If a trusted certificate or root is revoked, all global devices are updated, meaning users can trust that Windows will automatically protect against vulnerabilities in public key infrastructure. For cloud and enterprise deployments, Windows also offers users the ability to autoenroll and renew certificates in Active Directory with group policy to reduce the risk of potential outages due to certificate expiration or misconfiguration.
