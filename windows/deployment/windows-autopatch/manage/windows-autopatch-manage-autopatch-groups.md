---
title: Manage Windows Autopatch groups
description: This article explains how to manage Autopatch groups
ms.date: 08/05/2025
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

# Manage Windows Autopatch groups

Autopatch groups help Microsoft Cloud-Managed services meet organizations where they are in their update management journey.

An Autopatch group is a logical container or unit that groups several [Microsoft Entra groups](/entra/fundamentals/groups-view-azure-portal), and software update policies, such as [Update rings policy for Windows 10 and later](/mem/intune/protect/windows-10-update-rings), [feature updates for Windows 10 and later policies](/mem/intune/protect/windows-10-feature-updates), [driver update policies](../manage/windows-autopatch-manage-driver-and-firmware-updates.md), [Microsoft 365 App update policies](../manage/windows-autopatch-microsoft-365-policies.md), and [Microsoft Edge update policies](../manage/windows-autopatch-edge.md).

Before you start managing Autopatch groups, ensure you meet the [Windows Autopatch groups prerequisites](../deploy/windows-autopatch-groups-overview.md#prerequisites).

> [!NOTE]
> If you reach the maximum number of Autopatch groups supported (300), and try to create more Autopatch groups, the "Create" option in the Autopatch groups blade is greyed out.

## Create an Autopatch group

> [!IMPORTANT]
> Windows Autopatch creates the device-based Microsoft Entra ID assigned groups based on the choices made in the deployment ring composition page. Additionally, the service assigns the update ring policies for each deployment ring created in the Autopatch group based on the choices made in the Windows Update settings page as part of the Autopatch group guided end-user experience.

> [!TIP]
> For more information on workloads supported by Windows Autopatch groups, see [Supported software workloads](../deploy/windows-autopatch-groups-overview.md#software-update-workloads).

**To create an Autopatch group:**

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Select **Tenant administration** from the left navigation menu.
1. Under the **Windows Autopatch** section, select **Autopatch groups**.
1. In the **Autopatch groups** blade, select **Create**.
1. In the **Basics** page, enter a **name** and a **description** then select **Next: Deployment rings**.
    1. Enter up to 255 characters for the Autopatch group name and 150 characters maximum for the description. The Autopatch group name is appended to both the update rings and the DSS policy names that get created once the Autopatch group is created.
1. In the **Deployment rings** page, select **Add deployment ring** to add the number of deployment rings to the Autopatch group. Autopatch assigns a default rollout schedule to ensure gradual deployment with deferral and deadline periods ranging from one to 20 days. When a new ring is added, its default deferral and deadline are spaced with existing rings to maintain deferral and deadline period compliance. Therefore, the deferral and deadline period of the new ring might be before or after the previous ring. Adding a new ring doesn’t modify the deferral or deadline of already existing rings. Autopatch doesn’t set deadlines on Sundays. The deadline is scheduled for the following Monday.
1. Each new deployment ring added must have either a Microsoft Entra device group assigned to it, or a Microsoft Entra group that is dynamically distributed across your deployments rings using defined percentages.
    1. In the **Dynamic groups** area, select **Add groups** to select one or more existing device-based Microsoft Entra groups to be used for Dynamic group distribution.
    1. In the **Dynamic group distribution** column, select the desired deployment ring checkbox. Then, either:
        1. Enter the percentage of devices that should be added from the Microsoft Entra groups selected in step 9. The percentage calculation for devices must equal to 100%, or
        1. Select **Apply default dynamic group distribution** to use the default values.
1. In the **Assigned group** column, select **Add group to ring** to add an existing Microsoft Entra group to any of the defined deployment rings. The **Test** and **Last** deployment rings only support Assigned group distribution. These deployment rings don't support Dynamic distribution.
1. Select **Next: Update types**. Select the types of updates you want Windows Autopatch to create policies for. You can select:
    1. Quality updates
    1. Feature updates
    1. Driver updates
    1. Microsoft 365 apps updates
    1. Microsoft Edge updates
1. Select **Next: Deployment settings**. If you selected quality updates and Microsoft 365 apps updates in Step 9, these updates are deployed automatically. Use the dropdown menu to select:
    1. The target version for feature updates
    1. The approval method for driver updates
    1. The channel for Microsoft Edge updates
1. Select **Next: Release schedules**. In this page, select one of the following release schedule presets from the **Select a release schedule preset** dropdown menu:
    1. **Information worker**: Single-user devices that are used in most workplaces
    1. **Shared device**: Devices that are used by multiple users over a period of time
    1. **Kiosks and billboards**: High uptime devices used to accomplish a specific task that hides notifications and restart at specific times
    1. **Reboot-sensitive devices**: Devices that can’t be interrupted in the middle of a task and only update at a scheduled time
1. The Windows update installation, reboot, and notification behavior setting is based on the selected release schedule preset (in step 11). The setting determines how the Windows Update client behaves for all update types that you selected in Step 9. You can:
    1. Edit the deferrals, deadlines, grace periods as needed
    1. Edit the deployment rings as necessary
    1. If you made changes, but want to start over, select **Reset to preset values [release schedule preset]**. The reset is dependent on which release schedule preset you selected in step 12.
1. Select **Next: Scope tags**. Add the scope tags you want to assign for the Autopatch group. For more information on Scope tags, see [Scoped admins and Autopatch groups](../prepare/windows-autopatch-role-based-access-control.md#scoped-admins-and-autopatch-groups).
1. Select **Review + create** to review all changes made.
1. Once the review is done, select **Create** to save your Autopatch group.

> [!CAUTION]
> **Don't** modify the Microsoft Entra group membership types (Assigned and Dynamic). Otherwise, the Windows Autopatch service isn't able to read the device group membership from these groups, and causes the Autopatch groups feature and other service-related operations to not work properly.<p>Additionally, it's not supported to have Configuration Manager collections directly synced to any Microsoft Entra group created by Autopatch groups.</p>

> [!CAUTION]
> A device-based Microsoft Entra group can only be used with one deployment ring in an Autopatch group at a time. This applies to deployment rings within the same Autopatch group and across different deployment rings across different Autopatch groups. If you try to create or edit an Autopatch group to use a device-based Microsoft Entra group that is already used, an error occurs that prevents you from creating or editing the Autopatch group.

## Edit an Autopatch group

> [!TIP]
> You can't edit an Autopatch group when there's one or more Windows feature update releases targeted to it. If you try to edit an Autopatch group with one or more ongoing Windows feature update releases targeted to it, you get the following informational banner message: "**Some settings are not allowed to be modified as there's one or more ongoing Windows feature update release targeted to this Autopatch group.**"
> For more information on release and phase statuses, see [Windows feature update](../manage/windows-autopatch-windows-feature-update-overview.md).

**To edit an Autopatch group:**

1. Select the **horizontal ellipses (…)** > **Edit** for the Autopatch group you want to edit.
1. In the **Basics** page, you can only modify the **description** of an Autopatch group. You **can't** modify the name. Once the description is modified, or if you don't need to edit the description, select **Next: Deployment rings**. To rename an Autopatch group, see [Rename an Autopatch group](#rename-an-autopatch-group).
1. In the **Deployment rings** page, edit your deployment rings as necessary or select **Next: Update types**.
1. In the **Update types** page, add or remove update types as necessary, or select **Next: Deployment settings**.
1. In the **Deployment settings** page, edit the deployment settings as necessary, or select **Next: Release schedule**.
1. In the **Release schedule** page, edit the deferral and/or deadline day as necessary, or select **Next: Scope tags**. If you need to change the release schedule preset, you must create a new Autopatch group.
1. In the Scope tags page, edit the scope tags as necessary, or select **Next: Review + save**. For more information on Scope tags, see [Scoped admins and Autopatch groups](../prepare/windows-autopatch-role-based-access-control.md#scoped-admins-and-autopatch-groups).
1. Select **Review + create** to review all changes made.
1. Once the review is done, select **Save** to finish editing the Autopatch group.

> [!IMPORTANT]
> Windows Autopatch creates the device-based Microsoft Entra ID assigned groups based on the choices made in the deployment ring composition page. Additionally, the service assigns the update ring policies for each deployment ring created in the Autopatch group based on the choices made in the Windows Update settings page as part of the Autopatch group guided end-user experience.

> [!CAUTION]
> If a device that was previously added to an Autopatch group uses a Microsoft Entra group (via Assigned groups or Dynamic distribution method) is removed from the Microsoft Entra group, the device is removed and deregistered from the Autopatch service. The removed device no longer has any Autopatch service-created policies applied to it and the device doesn't appear in the [Autopatch groups membership report](../deploy/windows-autopatch-register-devices.md#autopatch-groups-membership-report).

## Rename an Autopatch group

**To rename an Autopatch group:**

1. Select the **horizontal ellipses (…)** > **Rename** for the Autopatch group you want to rename. The **Rename Autopatch group** fly-in opens.
1. In the **New Autopatch group name**, enter the new Autopatch group name of your choice, then select **Rename group**.

> [!IMPORTANT]
> Autopatch supports up to 255 characters for the Autopatch group name. Additionally, when you rename an Autopatch group all [update rings for Windows 10 and later policy in Intune](/mem/intune/protect/windows-10-update-rings) and [feature updates for Windows 10 and later policy in Intune](/mem/intune/protect/windows-10-feature-updates) associated with the Autopatch group are renamed to include the new Autopatch group name you define in its name string. Also, when renaming an Autopatch group all Microsoft Entra groups representing the Autopatch group's deployment rings are renamed to include the new Autopatch group name you define in its name string.

## Delete an Autopatch group

**To delete an Autopatch group:**

1. Select the **horizontal ellipses (…)** > **Delete** for the Autopatch group you want to delete.
1. Select **Yes** to confirm you want to delete the Autopatch group.

> [!CAUTION]
> You can't delete an Autopatch group when it's being used as part of one or more active or paused feature update releases. However, you can delete an Autopatch group when the release for either Windows quality or feature updates has either the **Scheduled** or **Paused** statuses.

## Manage device conflict scenarios when using Autopatch groups

Overlap in device membership is a common scenario when working with device-based Microsoft Entra groups. Sometimes dynamic queries can be large in scope or the same assigned device membership can be used across different Microsoft Entra groups.

Since Autopatch groups uses your existing Microsoft Entra groups to create your own deployment ring composition, the service takes on the responsibility of monitoring and automatically solving some of the device conflict scenarios that might occur.

> [!CAUTION]
> A device-based Microsoft Entra group can only be used with one deployment ring in an Autopatch group at a time. This applies to deployment rings within the same Autopatch group and across different deployment rings across different Autopatch groups. If you try to create or edit an Autopatch group to use a device-based Microsoft Entra group that is already used, an error occurs that prevents you from creating or editing the Autopatch group.

### Device conflict in deployment rings within an Autopatch group

Autopatch groups use the following logic to solve device conflicts on your behalf within an Autopatch group:

| Step | Description |
| -----  | ----- |
| Step 1: Checks for the deployment ring distribution type (**Assigned** or **Dynamic**) that the device belongs to. | For example, if a device is part of one deployment ring with **Dynamic** distribution (Ring3), and one deployment ring with **Assigned** distribution (Test) within the same Autopatch group, the deployment ring with **Assigned** distribution (Test) takes precedence over the one with the **Dynamic** distribution type (Ring3). |
| Step 2: Checks for deployment ring ordering when device belongs to one or more deployment ring with the same distribution type (**Assigned** or **Dynamic**) | For example, if a device is part of one deployment ring with **Assigned** distribution (Test), and in another deployment ring with **Assigned** distribution (Ring3) within the **same** Autopatch group, the deployment ring that comes later (Ring3) takes precedence over the deployment ring that comes earlier (Test) in the deployment ring order. |

> [!IMPORTANT]
> When a device belongs to a deployment ring that contains combined distribution types (**Assigned** and **Dynamic**), and a deployment ring that has only the **Dynamic** distribution type, the deployment ring with the combined distribution types takes precedence over the one with only the **Dynamic** distribution. If a device belongs to two deployment rings that contains combined distribution types (**Assigned** and **Dynamic**), the deployment ring that comes later takes precedence over the deployment ring that comes earlier in the deployment ring order.

### Device conflict across different Autopatch groups

Device conflict across different deployment rings in different Autopatch groups might occur, review the following examples about how the Windows Autopatch services handles the following scenarios:

#### Same device in different deployment rings across different Autopatch groups

| Conflict scenario | Conflict resolution |
| -----  | ----- |
| You, the IT admin at Contoso Ltd., are using several Autopatch groups. While navigating through devices in the Windows Autopatch Devices blade, you notice that the same device is part of different deployment rings across several different Autopatch groups. This device appears as **Not ready**. | You must resolve this conflict.<p>Autopatch groups inform you about the device conflict in the [**Autopatch groups membership report**](../deploy/windows-autopatch-register-devices.md#autopatch-groups-membership-report). Select the **Not ready** status for the device you want to address. You're required to manually indicate which of the existing Autopatch groups the device should exclusively belong to.</p> |

#### Device conflict before device registration

When you create or edit an Autopatch group, Windows Autopatch checks if the devices that are part of the Microsoft Entra groups, used in Autopatch groups’ deployment rings, are registered with the service.

| Conflict scenario | Conflict resolution |
| -----  | ----- |
| Device conflict before device registration due to device membership overlap | You must resolve this conflict.<p>Devices fail to register with the service and are marked with a **Not registered** status. You’re required to make sure the Microsoft Entra groups that are used in an Autopatch group don’t have device membership overlaps.</p> |
