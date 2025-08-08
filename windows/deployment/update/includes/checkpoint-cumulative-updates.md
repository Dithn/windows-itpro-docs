---
author: mestew
ms.author: mstewart
manager: bpardi
ms.subservice: itpro-updates
ms.service: windows-client
ms.topic: include
ms.date: 01/31/2025
ms.localizationpriority: medium
---
<!-- This file is used multiple times in release-cycle.md. Headings are driven by article context. 9693727-->

Starting Windows 11, version 24H2, Microsoft may periodically release cumulative updates as checkpoints. The subsequent updates will consist of:
- The update package files associated with the checkpoints, and
- New update package files that contain incremental binary differentials against the version of binaries in the last checkpoint.

Multiple checkpoints may be shipped during the lifecycle of a given Windows release. Devices updating from Windows Update and WSUS can continue to seamlessly install the latest monthly security update regardless of whether there are any preceding checkpoint cumulative updates, **no change is needed to their update process**. Catalog users can review [Checkpoint cumulative updates and Microsoft Update Catalog usage](../catalog-checkpoint-cumulative-updates.md) for reference.
