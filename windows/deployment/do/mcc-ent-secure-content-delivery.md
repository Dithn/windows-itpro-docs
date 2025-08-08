---
title: Microsoft Connected Cache for Enterprise and Education Secure Content Delivery
description: Details on how Microsoft Connected Cache for Enterprise and Education securely delivers content to requesting Delivery Optimization clients.
ms.service: windows-client
ms.subservice: itpro-updates
ms.topic: article
author: chrisjlin
ms.author: lichris
manager: naengler
ms.reviewer: mstewart
ms.collection:
  - tier3
ms.localizationpriority: medium
appliesto:
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 11</a>
- ✅ Supported Linux distributions
- ✅ <a href=https://learn.microsoft.com/windows/deployment/do/waas-microsoft-connected-cache target=_blank>Microsoft Connected Cache for Enterprise</a>	
- ✅ <a href=https://learn.microsoft.com/windows/deployment/do/waas-delivery-optimization target=_blank>Delivery Optimization</a>
ms.date: 03/19/2025
---

# Microsoft Connected Cache for Enterprise and Education Secure Content Delivery

This article describes how Connected Cache nodes facilitate secure delivery of Microsoft content between Microsoft/CDN endpoints and Delivery Optimization clients.

## How Connected Cache nodes facilitate secure content delivery

Connected Cache nodes act as transparent content caches, meaning any device can request Microsoft content from a Connected Cache node without needing to provide authentication of identity. This allows for efficient discovery and connectivity between devices and Connected Cache nodes on the same network.

Connected Cache nodes only download and store Microsoft content from provisioned Microsoft and Content Delivery Network (CDN) endpoints, so there are no concerns about the cache storing personal or sensitive data.

Connected Cache works in tandem with the [Delivery Optimization (DO) client](waas-delivery-optimization.md), a component of Windows that manages the downloading of Microsoft content. Regardless of download source, the DO client on each Windows device verifies the authenticity and integrity of downloaded content using its metadata hash and content hash. In addition, the downloaded content's signature is verified before it's installed. This process ensures that the Windows device is protected against man-in-the-middle attacks that attempt to tamper with content while it's in transit.

![Diagram of content delivery between CDN, cache node, and DO client](images/mcc-ent-secure-content-delivery-diagram.png)

As shown in the diagram, Connected Cache nodes currently utilize HTTP to communicate with CDN endpoints and Delivery Optimization clients. There's work planned to support HTTPS communication between CDN endpoints, Connected Cache nodes, and Delivery Optimization clients in the future for content that utilizes HTTPS.

## Security considerations for Connected Cache nodes

The security of each Connected Cache node is dependent on the security of its environment.

In order to securely function as designed, Connected Cache expects the user to take steps to secure the different components of their organization's network and devices.

The following section is intended to provide a high-level overview of some of the security aspects the user should consider and resources for learning more.

### Azure resources

One aspect of security lies with the Azure resources that your Microsoft Connected Cache nodes communicate with. You should ensure that your organization's Azure tenant is using role-based access control (RBAC) to apply policies that enforce least-privilege access to the Azure resources for Connected Cache that you provision. Only trusted individuals should have the ability to perform create, read, update, and delete (CRUD) operations on your organization's Connected Cache Azure resources and cache nodes.

You can learn more about the principles of Azure resource security by referring to the [Azure identity management and access control security best practices](/azure/security/fundamentals/identity-management-best-practices) and the [Microsoft cloud security benchmark (MCSB) documentation for Identity management](/security/benchmark/azure/mcsb-identity-management).

### Local network

Another aspect of security lies with your organization's local network. It's recommended that your organization adopts a Zero Trust approach to network security so that your organizational data is protected even if an attacker breaches your network perimeter.

One best practice is to utilize a firewall on your organization's network. When using a network firewall, you should configure it to allow communication between your Connected Cache nodes and the [Microsoft and CDN endpoints](delivery-optimization-endpoints.md) used to install Connected Cache and download Microsoft content.

You can learn more about the principles of network security by referring to the [Azure best practices for network security](/azure/security/fundamentals/network-best-practices) and the [Microsoft cloud security benchmark (MCSB) documentation for Network security](/security/benchmark/azure/mcsb-network-security).

### Cache node host machine OS

Another aspect of security lies with the operating system (OS) of your Connected Cache node's host machine. Your organization can choose to host Microsoft Connected Cache nodes on a [compatible host OS](mcc-ent-prerequisites.md#cache-node-host-machine-requirements) of your choice.

Regardless of which host OS you choose to use, you should ensure that you perform regular OS updates to keep it up to date.

If you're hosting on Windows, your host machine uses Windows Subsystem for Linux (WSL) to run the Connected Cache container. You should ensure that your deployment of WSL meets the [recommended Enterprise set up for WSL](/windows/wsl/enterprise).

### Organization-managed Windows devices

Another aspect of security lies with the organization-managed Windows devices that request Microsoft content from your Connected Cache nodes. The Windows devices that are connecting to the Connected Cache node should be secured according to your organization's security policy.

## Frequently asked questions

Here are some common questions you might have about the security of Microsoft Connected Cache for Enterprise and Education.

### How often is the Connected Cache container updated?

There might be several Connected Cache container updates per year. These updates may contain new features, bug fixes, and security patches. When a new Common Vulnerability and Exposure (CVE) is identified, Microsoft may release a new container update to address the vulnerability.

For more information about Connected Cache container updates and how to schedule their installation, see [Update Microsoft Connected Cache for Enterprise and Education](mcc-ent-update-cache-node.md).

### What security improvements are included in the latest Connected Cache container update?

You can find a list of security improvements and other fixes in the [Connected Cache release notes](mcc-ent-release-notes.md).

## Related content

- [Understand Windows Update security](/windows/deployment/update/windows-update-security)
- [Understand the Delivery Optimization secure workflow](delivery-optimization-workflow.md#download-request-workflow)
- [Understand delivery of Win32 apps via Intune](/troubleshoot/mem/intune/app-management/develop-deliver-working-win32-app-via-intune#the-flow-behind-delivery-of-a-win32-app-to-the-client)
- [Microsoft Win32 Content Prep Tool](https://github.com/Microsoft/Microsoft-Win32-Content-Prep-Tool)
