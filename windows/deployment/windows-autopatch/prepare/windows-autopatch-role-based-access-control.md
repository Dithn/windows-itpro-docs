---
title: Role-based access control
description: This article provides an overview on role-based access control in Windows Autopatch
ms.date: 05/27/2025
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

# Role-based access control

Use role-based access control in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) to manage who has access to your organization's resources and what they can do with those resources.

## Built-in roles

Windows Autopatch enables role-based access control to use the least privileged access to distribute and delegate Windows Update management in Microsoft Intune.

> [!IMPORTANT]
> To successfully manage Windows Autopatch as a lower privilege role, the user must have both Autopatch Admin permissions and Policy and Profile admin permissions.

The permissions defined in Windows Autopatch administrator or Windows Autopatch reader roles are used to manage Autopatch groups, support requests, Autopatch messages, and Autopatch reports.

To manage update policies and Windows Update reports, Device Configuration permission is **required**. This permission is available in built-in roles such as the Policy and Profile Manager roles.

### Policy and Profile Manager roles

Policy and Profile Manager roles include device configuration permissions for managing Intune policies including the following Update policies:

- Update rings
- Quality updates
- Feature updates
- Driver updates

### Windows Autopatch Administrator

The Windows Autopatch Administrator role manages all aspects of Windows Autopatch:

- [Autopatch groups](../deploy/windows-autopatch-groups-overview.md)
- [Autopatch reports](../monitor/windows-autopatch-windows-quality-and-feature-update-reports-overview.md)
    - Quality and feature update status and trending reports
- [Support requests and messages](../manage/windows-autopatch-support-request.md)

### Windows Autopatch Reader

Windows Autopatch Reader can view Windows Autopatch data available in Microsoft Intune but can't make changes.

### Update policy roles

To manage Windows quality update, update rings, Windows feature update, driver update, Microsoft 365 Apps, and Microsoft Edge policies the user must have full [Device Configuration permissions](/intune/intune-service/fundamentals/role-based-access-control-reference#policy-and-profile-manager). The following table is the full list of update management roles:

| Intune role | Update policies |
| --- | --- |
| Policy & Profile Manager | Read/Write |
| Helpdesk Operator | Read |
| Read-only Operator | Read |
| Autopatch Administrator | No permission |
| Autopatch Reader | No permission |

To successfully manage Windows Autopatch as a lower privilege role, the user must have both Autopatch Admin permissions and the Policy and Profile admin permissions.

### Microsoft Entra roles

The following Microsoft Entra roles can access Windows Autopatch features via the Microsoft Intune portal.

| Microsoft Entra role | All Windows Autopatch data | Tenant Administration > Windows Autopatch |
| --- | --- | --- |
| Global Administrator | Read/Write | Read/Write |
| Intune Service Administrator | Read/Write | Read/Write |
| Global Reader | Read | Read |
| Service Support Administrator | No permission | Read<p>Tenant Administration/Windows Autopatch/All</p> |
| Security Admin | No permission | Read<p>Tenant Administration/Windows Autopatch/All</p> |
| Security Reader | No permission | Read<p>Tenant Administration/Windows Autopatch/All</p> |
| Billing Administrator | No permission | Read<p>Tenant Administration/Windows Autopatch/All</p> |
| Helpdesk Administrator | No permission | Read<p>Tenant Administration/Windows Autopatch/All</p> |

### Custom roles

You can create two custom roles that include permissions required for a specific job role.

To achieve all-up update management, make sure that the groups assigned to the Autopatch custom role are also a member of the [Policy & Profile Manager role](#policy-and-profile-manager-roles) or a custom role with equivalent permissions.

Navigate to **Tenant Administration** > **Roles** > **Create Custom role** > **Windows Autopatch** to create a custom role.

| Permission | Description |
| --- | --- |
| Role Assignments/Create | Create an Autopatch role for operations that are performed on Autopatch resources. |
| Role Assignments/Update | Update role for Autopatch, where Edit operations are performed on Autopatch resources. |
| Role Assignments/Delete | Delete role for Autopatch, where delete operations are performed on Autopatch resources. |
| Roles/Read | View permissions, role definitions, and role assignments for Autopatch role. View operation or actions are performed on Autopatch resources. |
| Autopatch Groups/Read | Read Autopatch groups and its properties. |
| Autopatch Groups/Create | Create Autopatch groups, add group assignments, and configure release settings. |
| Autopatch Groups/Edit | Edit Autopatch groups, modify release settings, and manage group assignments. |
| Autopatch Groups/Delete | Delete Autopatch groups. |
| Reports/Read | Read and export Autopatch quality and feature update reports. |
| Reports/DiscoverDevices | Allows Device report action to discover devices. |
| Reports/AssignRing | Allows Device ring assignment to Autopatch groups. |
| Reports/ExcludeDevices | Perform exclude devices action on the Device reports. |
| Reports/RestoreExcludedDevices | Perform Restore action on the Device reports. |
| Support requests/Read | Read existing Autopatch support requests and responses. |
| Messages/Read | Read published Autopatch and Service Health Dashboard messages. |

### Scopes

Windows Autopatch supports Intune scope tags and scoped groups to be used for distributed update management. Use Microsoft Intune to create and manage scope tags.

- Windows Autopatch supports Intune scope for Autopatch groups, Autopatch role assignments, update policies, and reports.
- Autopatch messages, support, and Admin contacts don't support scopes.
- Autopatch groups created by scoped admins are assigned to the same scope tags as the user.
- Only scoped admins, with the same scope tags assigned to them, can edit and manage Autopatch groups.
- When you create Autopatch groups and assign scope tags, the update policies created inherit the same scope tags.
- The devices assigned to Autopatch groups don't inherit the Autopatch group scope tags. Use Intune to assign scope tag to devices.

## Permissions for Autopatch groups

Autopatch groups create Microsoft Entra groups and update policies and assign the policies to the group as part of its workflow. To successfully complete the workflow, both permissions are **required**. The option to create Autopatch groups is only available when the user has both the permissions enabled.

1. Device Configuration, **all** permissions
2. Windows Autopatch group, **all** permissions

Windows Autopatch groups that are assigned scoped tags are only visible to users with those exact scope tags. This ensures the IT admin can manage the ring-based rollouts using Autopatch groups and aren't affected by scope discrepancies.

> [!NOTE]
> The Autopatch group workflow creates deployment rings and assigns update policies to them. If the Autopatch role includes All devices in scope, the policy administration role must have [All devices and All Users](/intune/intune-service/fundamentals/role-based-access-control#role-assignments) in its scope.<p>Lack of Microsoft Entra permissions can prevent the logged-in user from creating Groups. The user must have sufficient permission to create Groups. For more information, see [How to set up self-service group management](/entra/identity/users/groups-self-service-management#make-a-group-available-for-user-self-service) or [Create Groups permissions](/entra/identity/role-based-access-control/custom-group-permissions#create-groups).</p>

When the user is assigned scoped groups, they can only assign scoped groups for distribution into deployment rings.

## Scoped admins and Autopatch groups

In Intune scoped admins, only an admin user that is assigned specific scope tags and Scoped Groups, can assign policies only to Scoped Groups.

> [!NOTE]
> Intune administrators or update administrators with All devices and All users scopes can't see the Pending assignment workflow; this only affects roles that have scopes assigned through specific Scoped Groups.

### Scoped admins and Autopatch group workflow

As part of the Autopatch group creation workflow, Windows Autopatch creates Microsoft Entra groups and update policies for the selected deployment settings. To assign the update policies to the newly created deployment rings, you must include the Autopatch group as a Scoped Group in the role that contains [Device Configuration permissions](/intune/intune-service/fundamentals/role-based-access-control-reference#policy-and-profile-manager).

> [!NOTE]
> An Intune administrator or a Role Administrator must assign the newly created Windows Autopatch group as a scoped group before the Autopatch group can be used by the scoped Admin.<p>Once the Autopatch group, in **Pending Assignment** status, is added as a scoped group, the scoped admin can assign the update policies the Autopatch group becomes **Active**.</p>

The following table explains the high-level workflow:

| Step | Description | Who |
| --- | --- | --- |
| Step 1: Create an Autopatch group | Create an Autopatch group. Autopatch groups register devices with the Windows Autopatch service when you either [create](../manage/windows-autopatch-manage-autopatch-groups.md#create-an-autopatch-group) or [edit an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#edit-an-autopatch-group).<p>The Autopatch group, deployment rings, and the update policies are created.</p><p>You can view the [update policies](/intune/intune-service/protect/windows-10-update-rings) under Windows updates.</p> | Scoped admin |
| Step 2: Contact your Intune Administrator or Role administrator to assign the Autopatch parent group as a Scoped Group for your role | Include the following information:<ul><li>The name of the Autopatch parent group. Select the **Pending Assignment** status flyout to find the name.</li><li>Your Intune role that has Device Configuration permissions for update management </li></ul>| Scoped admin |
| Step 3: Assign the Autopatch parent group as the Scoped Group for the role with Device Configuration permission | Add the Autopatch parent as the Scoped Group using [Assign scoped group](/intune/intune-service/fundamentals/scope-tags#to-assign-a-scope-tag-to-a-ro). | Intune Administrator or Intune Role Administrator |
| Step 4: Complete the policy assignments so Autopatch groups are ready for use | Select **Complete group assignments** if the Autopatch group remains in Pending assignment status, and the Assign scoped group step isn't yet complete.<p>Once the policy assignment is successful, the Autopatch group is set to **Active** and ready for use.</p><p>The Scoped group assignment might not be immediately available. It might take up to 10 minutes to take effect.</p> | Scoped admin |

### Assign scope tags to Autopatch groups

> [!NOTE]
> If you're assigning scope tags to existing Autopatch groups, the scope admin must be included as a Scoped Group in their role with [Device Configuration permissions](/intune/intune-service/fundamentals/role-based-access-control-reference#policy-and-profile-manager) to manage the Autopatch group.<p>Windows Autopatch creates a parent group that nests the Autopatch group and deployment rings which can be added as the Scoped Group. You can find the parent group name in the Autopatch group properties.</p>

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), navigate to **Tenant Administration** > **Autopatch groups** > **select a group**. All rings and policies of the Autopatch group have the same scope.
1. In the **Add group to ring** option, select the Microsoft Entra groups to be assigned to the Autopatch group. Only groups with scope objects are available for selection.
1. Navigate to **Properties** > **Scope (Tags)** > **Edit** > **Select scope tags** > select the tags that you want to add to the profile. You can assign a **maximum of 100 scope tags** to an object.
    1. The **Scope Group** section is displayed when the service detects Autopatch groups that are created before role-based access controls. This indicates that a Microsoft Entra group is created, which can be added as a Scoped Group. A scoped admin can manage this Autopatch group if included in their scope.
    2. Follow the steps in the [Scoped admins and Autopatch group workflow](#scoped-admins-and-autopatch-group-workflow) section to assign scoped groups.
1. Select **Review + save**.

## Known issues

Windows 365 Enterprise gives IT admins the option to [register devices with Windows Autopatch](../deploy/windows-autopatch-register-devices.md#windows-autopatch-on-windows-365-enterprise-workloads) as part of the Windows 365 provisioning policy creation. You must be an Intune Service administrator to complete this action.

### General troubleshooting

| Scenario | Message | Cause | Solution |
| --- | --- | --- | --- |
| You receive an error message when you try to [create](../manage/windows-autopatch-manage-autopatch-groups.md#create-an-autopatch-group), [edit](../manage/windows-autopatch-manage-autopatch-groups.md#edit-an-autopatch-group), or [delete an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#delete-an-autopatch-group). | You don't have sufficient permission to modify this Autopatch group. You can only modify Autopatch groups that match your assigned scope. This Autopatch group has additional assigned Scope tags that don't match your role assignment.<p>Or</p><p>The Autopatch group submission failed, and the logged in user has scope tags assigned.</p> | The problem occurs when you edit an Autopatch group, and the service detected a mismatch in your scope tags. | Verify the scope tags assigned to the Autopatch group and Policy assignment role. The Policy assignment role might have more scope tags but must include **all** the scope tags assigned to the Autopatch group. |
| You receive an error message when you choose a device and the *Assign ring device* action in the [Autopatch groups membership report](../deploy/windows-autopatch-register-devices.md#autopatch-groups-membership-report). | You don't have sufficient permission, or the scope required to assign devices. | The problem occurs when Autopatch is unable to populate the Autopatch group list, because of a mismatch in scope tags. | Verify the scope tags for the Autopatch groups and your role. Ensure they share at least **one** scope tag. |
| You receive an error message when you choose a device and the *Assign ring device* action in the [Autopatch groups membership report](../deploy/windows-autopatch-register-devices.md#autopatch-groups-membership-report). | You don't have sufficient Autopatch group permission to complete this action. The minimum of Autopatch Group Read permission is required. | To move devices between Autopatch deployment rings, you need permission to read Autopatch groups. | Ensure your role includes **Autopatch Group/Read permission**. Navigate to Tenant Administration > Roles > My permission. |
| You receive an error message when you select a device in the [Autopatch groups membership report](../deploy/windows-autopatch-register-devices.md#autopatch-groups-membership-report). | Access Denied | You don't have the Intune permission to view the properties of the device. | Ensure your role includes **Managed devices/Read permission**. Navigate to Tenant Administration > Roles > My permission. |
| You can only see the **Releases**, **Update rings**, and **Monitor** tabs when logged in as a delegated Windows Autopatch administrator. | | You don't have all the required permission to view Windows Update. | Ensure your role includes **Organization/Read permission**. Navigate to Tenant Administration > Roles > My permission. |
| You receive an error message when you try to edit a preexisting Autopatch group that was newly assigned a scope tag. You successfully added the parent scope group into the Policy assignment role. | You don't have sufficient permission to modify this Autopatch group. You can only modify Autopatch groups that match your assigned scope. This Autopatch group has additional assigned Scope tags that don't match your role assignment. | The issue occurs when the service detects that the logged in user "Assigned Entra Group" isn't in the scoped group for the Autopatch admin role. This happens with preexisting Autopatch groups. | Add the Assigned Entra group as the scoped group to the Autopatch admin role. |
