---
title: Microsoft 365 Apps for enterprise
description: This article explains how Windows Autopatch manages Microsoft 365 Apps for enterprise updates
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

# Microsoft 365 Apps for enterprise

## Service level objective

Windows Autopatch aims to keep at least 90% of eligible devices on a [supported version](/deployoffice/overview-update-channels#support-duration-for-monthly-enterprise-channel) of the Monthly Enterprise Channel (MEC) for the:

- [Enterprise Standard Suite](/deployoffice/about-microsoft-365-apps). The Enterprise Standard Suite includes Access, Excel, OneNote, Outlook, PowerPoint, and Word.
- Subscription versions of Microsoft Project and Visio desktop apps, for example, Project Plan 3 or Visio Plan 2.

Microsoft 365 Apps deployed on the [Monthly Enterprise Channel](/deployoffice/overview-update-channels#monthly-enterprise-channel-overview) are supported for two months.

> [!NOTE]
> [Microsoft Teams](../manage/windows-autopatch-teams.md) uses a different update channel from the rest of Microsoft 365 Apps.

## Device eligibility

For a device to be eligible for Microsoft 365 Apps for enterprise updates (both 32-bit and 64-bit versions), as a part of Windows Autopatch, they must meet the following criteria:

- The device must be turned on and have an internet connection.
- The device must be able to access the [required network endpoints](../prepare/windows-autopatch-configure-network.md#required-microsoft-product-endpoints) to reach the Office Content Delivery Network (CDN).
- There are no policy conflicts between Microsoft Autopatch policies and customer policies.
- The device must check into the Intune service in the last five days.
- If Microsoft 365 Apps are running, the apps must close for the update process to complete.

## Update release schedule

All devices registered for Windows Autopatch receive updates from the [Monthly Enterprise Channel](/deployoffice/overview-update-channels#monthly-enterprise-channel-overview). This practice provides your users with new features each month, and they receive just one update per month on a predictable release schedule. Updates are released on the second Tuesday of the month; these updates can include feature, security, and quality updates. These updates occur automatically and pulled directly from the Office Content Delivery Network (CDN).

Unlike Windows update, the Office CDN doesn't make the update available to all devices at once. Over the course of the release, the Office CDN gradually makes the update available to the whole population of devices. Windows Autopatch doesn't control the order in which updates are offered to devices across your estate. After the update downloads, there's a seven day [update deadline](../manage/windows-autopatch-microsoft-365-policies.md) that specifies how long the user has until the user must apply the update.

## Deployment rings

Since the Office CDN determines when devices are offered updates, Windows Autopatch doesn't use rings to control the rollout of these updates.

## End user experience

Windows Autopatch configures the following end user experiences:

- Behavior during updates
- Office client

### Behavior during updates

> [!NOTE]
> If Microsoft 365 Apps are running, the apps must close for the update process to complete.

Updates are only applied when Microsoft 365 Apps aren't running. Therefore, [end user notifications for Microsoft 365 Apps](/deployoffice/updates/end-user-update-notifications-microsoft-365-apps) usually appear when:

- The user is working in a Microsoft 365 App, such as Microsoft Outlook, and didn't closed it in several days.
- The update [deadline arrives](/deployoffice/updates/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) and the updates still aren't applied.

### Office client app configuration

To ensure that users are receiving automatic updates, Windows Autopatch prevents the user from opting out of automatic updates.

## Microsoft 365 Apps for enterprise update controls

With the expanded Autopatch group capabilities, you can choose to turn on Microsoft 365 Apps updates on a per Autopatch group level. Depending on your tenant settings, one of the following scenarios occurs:

- Tenants that previously turned on Autopatch Microsoft 365 Apps update, has the Microsoft 365 Apps updates Update Type checkbox selected and the updated policies applied to each Autopatch group.
- Tenants that previously turned off Autopatch Microsoft 365 Apps updates, or are new to Windows Autopatch, Autopatch Microsoft 365 Apps updates remain turned off.

If you [created an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#create-an-autopatch-group) and selected Microsoft 365 apps updates as a content type, the **Update Type** checkbox is **selected**, with new policies created, and any available old policies are removed. If you didn’t select Microsoft 365 apps updates as a content type upon creating an Autopatch group, the **Update Type** checkbox is **unselected**. Any available customized policies are retained and appear in the **Policies** tab.

### Turn on Microsoft 365 Apps updates

**To turn on Microsoft 365 Apps updates:**

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Navigate to **Tenant Administration** > **Windows Autopatch** > **Autopatch groups**.
1. Select an Autopatch group to modify (repeat these steps for each group). 
1. Next to **Update types**, select **Edit**. 
1. Select **Microsoft 365 Apps updates**. 
1. Select **Next: Deployment settings** > **Next: Release schedules** > **Next: Review + save** > **Save** to save these changes.
1. We recommend deleting old Autopatch default policies to avoid policy conflict. Navigate to **Devices** > **Manage devices** > **Configuration** > **Policies** tab. 
1. Manually remove the following profiles related to Microsoft 365 Apps:
    1. Windows Autopatch - Office Configuration
    2. Windows Autopatch - Office Update Configuration [Test]
    3. Windows Autopatch - Office Update Configuration [First]
    4. Windows Autopatch - Office Update Configuration [Fast]
    5. Windows Autopatch - Office Update Configuration [Broad]

> [!NOTE]
> If you previously selected **Microsoft 365 Apps updates** when [creating an Autopatch group](../manage/windows-autopatch-manage-autopatch-groups.md#create-an-autopatch-group), but your tenant isn't showing the new updates, there’s a possibility that you previously modified the policy. To ensure there are no disruptions, the Autopatch Service retains that policy.

### Turn off Microsoft 365 Apps updates

**To turn off Microsoft 365 Apps updates:**

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Navigate to **Tenant Administration** > **Windows Autopatch** > **Autopatch groups**.
1. Select an Autopatch group to modify (repeat these steps for each group). 
1. Next to **Update types**, select **Edit**.
1. Unselect **Microsoft 365 Apps updates**. 
1. Select **Next: Deployment settings** > **Next: Release schedules** > **Next: Review + save** > **Save** to save these changes.

### Verify Microsoft 365 Apps updates policies

**To verify Microsoft 365 Apps updates policies:**

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Navigate to **Tenant Administration** > **Windows Autopatch** > **Autopatch groups**. 
1. Verify each Autopatch group has the **Microsoft 365 Apps Update Type** checkbox **selected**.
1. Navigate to **Devices** > **Manage devices** > **Configuration** > **Policies** tab.
1. The following new policies should be discoverable from the list of profiles:
    1. `"Windows Autopatch Microsoft 365 Update Policy - <group name> - <ring name>"`
1. The following profiles should be removed from your list of profiles and no longer visible/active. Use the Search with the keywords "Office Configuration". The result should return *0 profiles filtered*.
    1. Windows Autopatch - Office Configuration
    2. Windows Autopatch - Office Update Configuration [Test]
    3. Windows Autopatch - Office Update Configuration [First]
    4. Windows Autopatch - Office Update Configuration [Fast]
    5. Windows Autopatch - Office Update Configuration [Broad]

### Verify Microsoft 365 Apps updates policies are created

**To verify Microsoft 365 Apps updates policies are created:**

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Navigate to **Devices** > **Manage devices** > **Configuration** > **Policies**.
1. Confirm the new policies are named:`"Windows Autopatch Microsoft 365 Update Policy - <group name> - <ring name>"`

### Roll back a Microsoft 365 App update

Windows Autopatch doesn't allow you to pause or roll back an update in the Microsoft Intune admin center.

> [!NOTE]
> Updates are bundled together into a single release in the [Monthly Enterprise Channel](/deployoffice/overview-update-channels#monthly-enterprise-channel-overview). Therefore, we can't roll back only a portion of the update for Microsoft 365 Apps for enterprise.

## Compatibility with Servicing Profiles

[Servicing profiles](/deployoffice/admincenter/servicing-profile) is a feature in the [Microsoft 365 Apps admin center](https://config.office.com/) that provides controlled update management of monthly Office updates, including controls for user and device targeting, scheduling, rollback, and reporting.

A [service profile](/deployoffice/admincenter/servicing-profile#compatibility-with-other-management-tools) takes precedence over other policies, such as a Microsoft Intune policy or the Office Deployment Tool. The servicing profile affects all devices that meet the [device eligibility requirements](#device-eligibility) regardless of existing management tools in your environment. So, if you're targeting a managed device with a servicing profile it's ineligible for Microsoft 365 App update management. However, the device might still be eligible for other managed updates.

## Incidents and outages

If you're experiencing issues related to Microsoft 365 Apps for enterprise updates, [submit a support request](../manage/windows-autopatch-support-request.md). You can only submit a support request if you have E3+ or F licenses. For more information, see [Features and capabilities](../overview/windows-autopatch-overview.md#features-and-capabilities).
