---
title: Maintain the Windows Autopatch environment
description: This article details how to maintain the Windows Autopatch environment
ms.date: 03/31/2025
ms.service: windows-client
ms.subservice: autopatch
ms.topic: how-to
ms.localizationpriority: medium
author: tiaraquan
ms.author: tiaraquan
manager: bpardi
ms.reviewer: smithcharles
ms.collection:
  - highpri
  - tier1
---

# Maintain the Windows Autopatch environment

If any of the following items apply to your environment, make the adjustments as described.

> [!NOTE]
> If you make changes to policies in Microsoft Intune, Microsoft Entra ID, or Microsoft 365 that affect Windows Autopatch, it's possible that Windows Autopatch could stop operating properly.

## Windows Autopatch tenant management

### Windows Autopatch tenant actions

The Tenant management blade presents IT admins with any actions that are required to maintain Windows Autopatch service health. The **Tenant management** blade can be found by navigating to **Tenant administration** > **Windows Autopatch** > **Tenant management**.

> [!IMPORTANT]
> If you have any critical actions in your tenant, you must take action as soon as possible. When a critical action is active, you might not be able to use Windows Autopatch features, and your tenant may be considered [**inactive**](#inactive-status) by the service.

The type of banner that appears depends on the severity of the action. Currently, only critical actions are listed.

### Tenant action severity types

| Severity | Description |
| ----- | ----- |
| Critical | You must take action as soon as possible to avoid disruption to the Windows Autopatch service.<p>If no action is taken, you might lose access to Windows Autopatch features and your tenant could be marked as [**inactive**](#inactive-status).</p><p>To restore service health and return to an active status, all critical pending actions must be resolved.</p> |

### Critical actions

| Action type | Severity | Description |
| ----- | ----- | ----- |
| Maintain tenant access | Critical | Required licenses expired. The licenses include:<ul><li>Microsoft Intune</li><li>Microsoft Entra ID P1 or P2</li><li>Microsoft 365 Business Premium</li><li>Windows 10/11 Education A3 or higher </li><li>Windows 10/11 Enterprise E3 or higher</li><ul><li>For more information about specific services plans, see [Windows Autopatch Prerequisites](../prepare/windows-autopatch-prerequisites.md)</li></ul><p>To take action on missing licenses, you can visit the Microsoft 365 admin center or contact your Microsoft account manager. Until you renew the required licenses to run the service, Windows Autopatch marks your tenant as **inactive**. For more information, see [Microsoft 365 - What happens after my subscription expires?](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires)</p> |

### Inactive status

> [!NOTE]
> Only the Windows Autopatch sections of your tenant are marked as **inactive**.

When Windows Autopatch is **inactive**, you're alerted with banners on all Windows Autopatch blades. You're alerted with banners on all Windows Autopatch blades and have minimal access to Windows Autopatch features.

To be taken out of the **inactive** status, you must [resolve any critical actions shown in the Tenant management blade](#critical-actions).

> [!NOTE]
> Once critical actions are resolved, it can take up to two hours for Windows Autopatch to return to an **active** state.
