---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## :::image type="icon" source="../images/onedrive.svg" border="false"::: OneDrive for work or school

OneDrive for work or school is a cloud storage service that allows users to store, share, and collaborate on files. It's a part of Microsoft 365 and is designed to help organizations protect their data and comply with regulations. OneDrive for work or school is protected both in transit and at rest.

When data transits either into the service from clients or between datacenters, it's protected using transport layer security (TLS) encryption. OneDrive only permits secure access.

Authenticated connections aren't allowed over HTTP and instead redirect to HTTPS.

There are several ways that OneDrive for work or school is protected at rest:

- Physical protection: Microsoft understands the importance of protecting customer data and is committed to securing the datacenters that contain it. Microsoft datacenters are designed, built, and operated to strictly limit physical access to the areas where customer data is stored. Physical security at datacenters is in alignment with the defense-in-depth principle. Multiple security measures are implemented to reduce the risk of unauthorized users accessing data and other datacenter resources. Learn more [here](/compliance/assurance/assurance-datacenter-physical-access-security).
- Network protection: The networks and identities are isolated from the corporate network. Firewalls limit traffic into the environment from unauthorized locations
- Application security: Engineers who build features follow the security development lifecycle. Automated and manual analyses help identify possible vulnerabilities. The [Microsoft Security Response Center](https://technet.microsoft.com/security/dn440717.aspx) helps triage incoming vulnerability reports and evaluate mitigations. Through the [Microsoft Cloud Bug Bounty Terms](https://technet.microsoft.com/dn800983), people across the world can earn money by reporting vulnerabilities
- Content protection: Each file is encrypted at rest with a unique AES-256 key. These unique keys are encrypted with a set of master keys that are stored in Azure Key Vault

[!INCLUDE [learn-more](learn-more.md)]

- [How OneDrive safeguards data in the cloud](https://support.microsoft.com/topic/23c6ea94-3608-48d7-8bf0-80e142edd1e1)
