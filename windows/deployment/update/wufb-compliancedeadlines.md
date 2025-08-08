---
title: Enforce compliance deadlines with policies
description: This article contains information on how to enforce compliance deadlines using Windows Update client policies.
ms.service: windows-client
ms.subservice: itpro-updates
ms.topic: article
author: mestew
ms.localizationpriority: medium
ms.author: mstewart
manager: bpardi
appliesto:
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 11</a>
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 10</a>
ms.date: 03/18/2025
---
# Enforcing compliance deadlines for updates

Deploying feature or quality updates for many organizations is only part of the equation for managing their device ecosystem. The ability to enforce update compliance is the next important part. Windows Update client policies provide controls to manage deadlines for when devices should migrate to newer versions. This article contains information on how to enforce compliance deadlines for clients that use Windows Update client policies.

## Policies for compliance deadlines

# [Policies for Windows 11, version 22H2 and later](#tab/w11-22h2-policy)

### Policies for clients running Windows 11, version 22H2 and later

With Windows 11, version 22H2 and later, the following policies are available to manage compliance deadlines for updates:

|Policy| Description |
|-|-|
| **Specify deadline for automatic updates and restarts for quality update** | This policy lets you specify the number of days before quality  updates are installed on devices automatically, and a grace period, after which required restarts occur automatically. This policy includes an option to opt out of automatic restarts until the end of the grace period is reached. |
| **Specify deadline for automatic updates and restarts for feature update** | This policy lets you specify the number of days before feature updates are installed on devices automatically, and a grace period, after which required restarts occur automatically. This policy includes an option to opt out of automatic restarts until the end of the grace period is reached. |

In MDM, these policies are available as separate settings:
- [Update/ConfigureDeadlineForFeatureUpdates](/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)
- [Update/ConfigureDeadlineForQualityUpdates](/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)
- [Update/ConfigureDeadlineGracePeriod](/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod) (for quality updates)
- [Update/ConfigureDeadlineGracePeriodForFeatureUpdates](/windows/client-management/mdm/policy-csp-update#configuredeadlinegraceperiodforfeatureupdates) <!--Windows 11, version 22H2 and later-->
- [Update/ConfigureDeadlineNoAutoRebootForQualityUpdates](/windows/client-management/mdm/policy-csp-update#configuredeadlinenoautorebootforqualityupdates) <!--Windows 11, version 22H2 and later-->
- [Update/ConfigureDeadlineNoAutoRebootForFeatureUpdates](/windows/client-management/mdm/policy-csp-update#configuredeadlinenoautorebootforfeatureupdates) <!--Windows 11, version 22H2 and later-->

When **Specify deadline for automatic updates and restarts** for either quality updates or feature updates is set:

The deadline calculation for both quality and feature updates is based off the time the client's update scan initially discovered the update. Previously, the deadline was based off the release date of the update for quality updates and the reboot pending date for feature updates. The change for deadline calculation was made to improve the predictability of restart.

The grace period for both quality and feature updates starts its countdown from the time of a pending restart after the installation is complete. This grace period is especially helpful for users returning from vacation or the time away, preventing an immediate forced reboot when they come back.

The *effective deadline* is whichever is the later of the scan discovery time plus the specified deadline or the scan discovery time plus the grace period. As soon as installation is complete and the device reaches pending restart, users are able to schedule restarts before effective deadline and Windows can still automatically restart outside of active hours if users choose not to schedule restarts. Once the effective deadline is reached, the device tries to restart regardless of active hours.

> [!NOTE]
> - When these policies are used, [user settings for notifications](waas-wufb-csp-mdm.md#user-settings-for-notifications) are also used on clients running Windows 11, version 22H2 and later.
> - When **Specify deadline for automatic updates and restarts** for either quality updates or feature updates is used, updates will be downloaded and installed as soon as they are offered.
> - When **Specify deadline for automatic updates and restarts** for either quality updates or feature updates is used, download, installation, and reboot settings stemming from the [Configure Automatic Updates](waas-restart.md#schedule-update-installation) are ignored.
>    - Starting with the December 10, 2024 update for Windows 11, version 22H2 and later clients, [Configure Automatic Updates](waas-restart.md#schedule-update-installation) are respected before the deadline occurs, and ignored once the deadline passes. For instance, if you set up [Configure Automatic Updates](waas-restart.md#schedule-update-installation) to schedule update installation at 3:00 AM, you also set up a commercial deadline, then the download and install occurs at the scheduled time from [Configure Automatic Updates](waas-restart.md#schedule-update-installation) so long as it's not past the deadline.


# [Policies for Windows 10, version 22H2](#tab/w10-2h2-policy)

### Policies for clients running Windows 10, version 22H2
<!-- also applies to Windows 11, version 21H2 and earlier -->
With Windows 10, version 22H2, the following policies are available to manage compliance deadlines for updates:

|Policy|Description |
|-|-|
| Specify deadlines for automatic updates and restarts | This policy includes a deadline and a configurable grace period with the option to opt out of automatic restarts until the deadline is reached. This is the recommended policy for Windows 10, version 1709 and later.|

In MDM, these policies are available as separate settings:

- [Update/ConfigureDeadlineForFeatureUpdates](/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)
- [Update/ConfigureDeadlineForQualityUpdates](/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)
- [Update/ConfigureDeadlineGracePeriod](/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)
- [Update/ConfigureDeadlineGracePeriodForFeatureUpdates](/windows/client-management/mdm/policy-csp-update#configuredeadlinegraceperiodforfeatureupdates)
- [Update/ConfigureDeadlineNoAutoReboot](/windows/client-management/mdm/policy-csp-update#configuredeadlinenoautoreboot)

### Suggested configurations for clients running Windows 10, version 22H2

|Policy|Location|Quality update deadline in days|Feature update deadline in days|Grace period in days|
|-|-|-|-|-|
| Specify deadlines for automatic updates and restarts | GPO: Computer Configuration > Administrative Templates > Windows Components > Windows Update > Specify deadlines for automatic updates and restarts  | 2 | 2 | 3 |

When **Specify deadlines for automatic updates and restarts** is set (Windows 10, version 1709 and later):

For feature updates, the deadline and grace period start their countdown from the time of a pending restart after the installation is complete. As soon as installation is complete and the device reaches pending restart, the device tries to update outside of active hours. Once the *effective deadline* is reached, the device tries to restart during active hours. (The effective deadline is whichever is the later of the restart pending date plus the specified deadline or the restart pending date plus the grace period.)

For quality updates, the deadline countdown starts from the time the update is *offered* (not downloaded or installed). The grace period countdown starts from the time of the pending restart. The device tries to download and install the update at a time based on your other download and installation policies (the default is to automatically download and install in the background). When the pending restart time is reached, the device notifies the user and tries to update outside of active hours. Once the effective deadline is reached, the device tries to restart during active hours.

> [!NOTE]
> - When using the newer policy that contains **Feature updates grace period in days**, this setting is ignored by clients that are running Windows 11 version 21H2 and earlier. The grace period for quality updates is used for both quality updates and feature updates for these clients.
> - When **Specify deadlines for automatic updates and restarts** is used, download, installation, and reboot settings stemming from the [Configure Automatic Updates](waas-restart.md#schedule-update-installation) are ignored.

---

## User experience for restart notifications with compliance deadlines

<!--using include for restart notifications for compliance deadlines-->
[!INCLUDE [Restart notifications for compliance deadlines](./includes/wufb-restart-notifications-compliance-deadlines.md)]
