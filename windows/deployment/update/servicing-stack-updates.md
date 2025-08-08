---
title: Servicing stack updates
description: In this article, learn how servicing stack updates improve the code that installs the other updates.
ms.service: windows-client
ms.subservice: itpro-updates
ms.topic: article
author: mestew
ms.author: mstewart
manager: bpardi
ms.collection:
  - highpri
  - tier2
ms.localizationpriority: high
appliesto:
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 11</a>
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 10</a>
- ✅ <a href=https://learn.microsoft.com/windows/release-health/windows-server-release-info target=_blank>Windows Server </a>
ms.date: 1/22/2025
---

# Servicing stack updates

## What is a servicing stack update?

Servicing stack updates provide fixes to the servicing stack, the component that installs Windows updates. Additionally, it contains the component-based servicing stack (CBS), which is a key underlying component for several elements of Windows deployment, such as:

- Deployment Image Servicing and Management (DISM)
- System File Checker (SFC)
- Changing Windows features or roles
- Component repair

[CBS](https://techcommunity.microsoft.com/t5/ask-the-performance-team/understanding-component-based-servicing/ba-p/373012) is a small component that typically doesn't have updates released every month.


## What's the difference between a servicing stack update and a cumulative update?

Both Windows client and Windows Server use the cumulative update mechanism, in which many fixes to improve the quality and security of Windows are packaged into a single update. Each cumulative update includes the changes and fixes from all previous updates. A servicing stack update improves the reliability of the update process to mitigate potential issues while installing the latest monthly security update release and feature updates.

Starting in February 2021, the cumulative update includes the latest servicing stack updates, providing a single combined cumulative update payload for Windows Update, Windows Server Update Services (WSUS), and the Microsoft Update Catalog. This combined monthly cumulative update is available on Windows 10, version 2004 and later starting with [KB4601382](https://support.microsoft.com/kb/4601382). If you use an endpoint management tool backed by WSUS, such as Configuration Manager, you only have to select and deploy the monthly cumulative update. The latest servicing stack updates are automatically applied correctly. Release notes and file information for cumulative updates, including notes and information related to the servicing stack, are in a single KB article.


## When are they released?

Changes in the servicing stack are developed and released as part of the monthly cumulative update depending on new issues or vulnerabilities. In rare occasions, a prerequisite servicing stack update might need to be released out of band to address an issue impacting systems installing the monthly cumulative update. Out of band servicing stack updates are classified as Security with a severity rating of Critical.

