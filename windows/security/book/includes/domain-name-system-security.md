---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Domain Name System (DNS) security

In Windows 11, the Windows DNS client supports DNS over HTTPS and DNS over TLS, two encrypted DNS protocols. These allow administrators to ensure their devices protect their
name queries from on-path attackers, whether they're passive observers logging browsing behavior or active attackers trying to redirect clients to malicious sites. In a Zero Trust
model where no trust is placed in a network boundary, having a secure connection to a trusted name resolver is required.

Windows 11 provides group policy and programmatic controls to configure DNS over HTTPS behavior. As a result, IT administrators can extend existing security to adopt new models such as Zero Trust. IT administrators can mandate DNS over HTTPS protocol, ensuring that devices that use insecure DNS will fail to connect to network resources. IT administrators also have the option not to use DNS over HTTPS or DNS over TLS for legacy deployments where network edge appliances are trusted to inspect plain-text DNS traffic. By default, Windows 11 will defer to the local administrator on which resolvers should use encrypted DNS.

Support for DNS encryption integrates with existing Windows DNS configurations such as the Name Resolution Policy Table (NRPT), the system Hosts file, and resolvers specified per network adapter or network profile. The integration helps Windows 11 ensure that the benefits of greater DNS security do not regress existing DNS control mechanisms.
