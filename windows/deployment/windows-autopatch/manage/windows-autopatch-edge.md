---
title: Microsoft Edge
description: This article explains how Microsoft Edge updates are managed in Windows Autopatch
ms.date: 03/31/2025
ms.service: windows-client
ms.subservice: autopatch
ms.topic: how-to
ms.localizationpriority: medium
author: tiaraquan
ms.author: tiaraquan
manager: bpardi
ms.reviewer: hathind
ms.collection:
  - highpri
  - tier1
---

# Microsoft Edge

Windows Autopatch uses the [Stable Channel](/deployedge/microsoft-edge-channels#stable-channel) of Microsoft Edge.

## Device eligibility

For a device to be eligible for Microsoft Edge updates as a part of Windows Autopatch, they must meet the following criteria:

- The device must be powered on and have an internet connection.
- There are no policy conflicts between Windows Autopatch policies and customer policies.
- The device must be able to access the required network endpoints to reach the Microsoft Edge update service.
- If Microsoft Edge is open, it must restart for the update process to complete.

## Microsoft Edge update controls

With the expanded Autopatch group capabilities, you can choose to enable Microsoft Edge updates on a per Autopatch group level. Depending on your tenant settings, one of the following scenarios occurs:

- Tenants that previously turned on Autopatch Microsoft Edge updates, has the Microsoft Edge updates Update Type checkbox selected, and the updated policies applied to each Autopatch group.
- Tenants that previously turned off Autopatch Microsoft Edge updates, or are new to Windows Autopatch, Autopatch Microsoft Edge updates remain turned off.

If you [created an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#create-an-autopatch-group) and selected Microsoft Edge updates as a content type, the **Update Type** checkbox is **selected**, with new policies created and any available old policies are removed. If you didn’t select Microsoft Edge updates as a content type upon creating an Autopatch group, the **Update Type** checkbox is **unselected**. Any available customized policies are retained and appear in the **Policies** tab.

### Turn on Microsoft Edge updates

**To turn on Microsoft Edge updates:**

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Navigate to **Tenant Administration** > **Windows Autopatch** > **Autopatch groups**.
1. Select an Autopatch group to modify (repeat these steps for each group). 
1. Next to **Update types**, select **Edit**. 
1. Select **Microsoft Edge updates**. 
1. Select **Next: Deployment settings** > **Next: Release schedules** > **Next: Review + save** > **Save** to save these changes.
1. We recommend deleting old Autopatch default policies to avoid policy conflict. Navigate to **Devices** > **Manage devices** > **Configuration** > **Policies** tab. 
1. Manually remove the following profiles related to Microsoft Edge
    1. Windows Autopatch - Microsoft Edge Update Channel Beta
    1. Windows Autopatch - Microsoft Edge Update Channel Stable

> [!NOTE]
> If you previously selected **Microsoft Edge updates** when [creating an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#create-an-autopatch-group), but your tenant isn't showing the new updates, there’s a possibility that you previously modified the policy. To ensure there are no disruptions, the Autopatch Service retains that policy.

### Turn off Microsoft Edge updates

**To turn off Microsoft Edge updates:**

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Navigate to **Tenant Administration** > **Windows Autopatch** > **Autopatch groups**.
1. Select an Autopatch group to modify (repeat these steps for each group). 
1. Next to **Update types**, select **Edit**.
1. Unselect **Microsoft Edge updates**. 
1. Select **Next: Deployment settings** > **Next: Release schedules** > **Next: Review + save** > **Save** to save these changes.

### Verify Microsoft Edge updates policies

**To verify Microsoft Edge updates policies:**

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Navigate to **Tenant Administration** > **Windows Autopatch** > **Autopatch groups**. 
1. Verify each Autopatch group has the **Microsoft Edge Update Type** checkbox **selected**.
1. Navigate to **Devices** > **Manage devices** > **Configuration** > **Policies** tab.
1. The following new policies should be discoverable from the list of profiles:
    1. `"Windows Autopatch Microsoft Edge Update Policy - <group name> - <ring name>"`
1. The following profiles should be removed from your list of profiles and no longer visible/active. Use the Search with the keywords "Microsoft Edge Update Channel". The result should return *0 profiles filtered*.
    1. Windows Autopatch - Edge Update Channel Beta
    1. Windows Autopatch - Edge Update Channel Stable

### Verify Microsoft Edge updates policies are created

**To verify Microsoft Edge updates policies are created:**

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Navigate to **Devices** > **Manage devices** > **Configuration** > **Policies**.
1. Confirm the new policies are named:`"Windows Autopatch Microsoft Edge Update Policy - <group name> - <ring name>"`

## Update release schedule

Microsoft Edge checks for updates every 10 hours. Quality updates occur weekly by default. The Microsoft Edge product group [progressively](/deployedge/microsoft-edge-update-progressive-rollout) rolls out feature updates automatically every four weeks to ensure the best experience for customers. The update is available within a few days of the initial release.

Browser updates with critical security fixes have a faster rollout cadence than updates that don't have critical security fixes to ensure fast protection from vulnerabilities.

Devices in the Test device group receive feature updates from the [Beta Channel](/deployedge/microsoft-edge-channels#beta-channel). This channel is fully supported and automatically updated with new features approximately every four weeks.

## Pause and resume updates

Currently, Windows Autopatch can't pause or resume Microsoft Edge updates.

## Incidents and outages

If you're experiencing issues related to Microsoft Edge updates, [submit a support request](../operate/windows-autopatch-support-request.md). You can only submit a support request if you have E3+ or F licenses. For more information, see [Features and capabilities](../overview/windows-autopatch-overview.md#features-and-capabilities).
