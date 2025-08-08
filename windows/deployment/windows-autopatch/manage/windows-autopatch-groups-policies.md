---
title: Autopatch group policies
description: This article describes Autopatch group policies
ms.date: 03/31/2025
ms.service: windows-client
ms.subservice: autopatch
ms.topic: how-to
ms.localizationpriority: medium
author: tiaraquan
ms.author: tiaraquan
manager: bpardi
ms.reviewer: andredm7
ms.collection:
  - highpri
  - tier1
---

# Autopatch group policies

The following Autopatch group policies are only created when you create an Autopatch group.

## Update rings policy for Windows 10 and later

Autopatch groups create one Windows 10 Update Ring policy for each deployment ring you specify. These rings configure important update settings like automatic update behavior, deferrals, deadlines, and grace periods. See the following preset default policy values for restart-sensitive devices where the deadline and grace period aren't configured.

| Policy name | Quality updates deferral in days | Feature updates deferral in days | Feature updates uninstall window in days | Deadline for quality updates in days | Deadline for feature updates in days | Grace period | Auto restart before deadline |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| Test | 0 | 0 | 30 | 0 | 5 | 0 | Yes |
| Ring 1 | 1 | 0 | 30 | 2 | 5 |2 | Yes |
| Ring 2 | 5 | 0 | 30 | 2 | 5 | 2 | Yes |
| Ring 3 | 9 | 0 | 30 | 5 | 5 | 2 | Yes |
| Last | 10 | 0 | 30 | 3 | 5 | 2 | Yes |

## Feature update policy for Windows 10 and later

If features updates are [selected as a content type for an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#create-an-autopatch-group), a feature update policy is created with the Microsoft Entra groups for each update ring assigned to it. This policy does the following:

- Ensures existing devices on the target version don’t update beyond that version.
- If new devices are added to the Autopatch group and are below your target version, the devices are updated to the target version.

To achieve this outcome, the feature update policy is configured for immediate start as required.

> [!IMPORTANT]
> To safely deploy a new feature update, Autopatch recommends using a custom Windows feature update release. The custom release allows you to choose how and when different deployment rings receive the update. Autopatch doesn't recommend updating the minimum version within an Autopatch group until your rollout is complete. Doing so initiates a rollout which starts immediately for all members of that group.<p>Once you create a custom Windows feature update release, the Autopatch group's deployment rings are unassigned from that group’s feature update policy.</p>
