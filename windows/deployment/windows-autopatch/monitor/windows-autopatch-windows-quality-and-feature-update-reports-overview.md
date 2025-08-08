---
title: Windows quality and feature update reports overview
description: This article details the types of reports available and info about update device eligibility, device update health, device update trends in Windows Autopatch.
ms.date: 05/27/2025
ms.service: windows-client
ms.subservice: autopatch
ms.topic: overview
ms.localizationpriority: medium
author: tiaraquan
ms.author: tiaraquan
manager: bpardi
ms.reviewer: adnich
ms.collection:
  - highpri
  - tier1
---

# Windows quality and feature update reports overview

## Prerequisites

Windows Autopatch requires, and uses Windows diagnostic data to display device update statuses in Autopatch reports.

- Service state and substate data are included for all devices configured for Windows quality and feature updates. No data collection configuration is required.
- Client and substate data are collected from devices only if Windows data collection data is properly configured.

This data collection configuration method using Windows diagnostic data in Intune is shared across Autopatch reports. To support Autopatch reporting, you must configure the [Enable Windows diagnostic data collection settings](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#diagnostic-data-settings) from devices at the **Required** or higher level.

### Permissions and scope to view reports 

To view Windows Update reports, you must be assigned an Intune role with the **Device Configuration** > **View reports** permission. This permission is included in the following built-in roles:

- Policy and Profile Manager
- Read Only Operator
- Helpdesk Operator

In addition, the following roles have **Reports** > **Read permissions**. This permission is included in the following built-in roles, to access Windows Autopatch reports.

- Windows Autopatch Administrator
- Windows Autopatch reader

The report displays data based on device scope tags only. Therefore, Windows Update reports might include Update policies and Autopatch group information that aren't in the same scope as the device. For more information, see [role-based access control](../prepare/windows-autopatch-role-based-access-control.md) in Windows Autopatch.

To ensure accurate display of reports information, ensure that the Autopatch groups, update policies are accurately assigned to the same scope as the device.

## Windows quality update reports

The Windows quality reports provide you with information about:

- Quality update device readiness
- Device update health
- Device update alerts

Together, these reports provide insight into the quality update state and compliance of Intune devices.

The Windows quality report types are organized into the following focus areas:

| Focus area | Description |
| ----- | ----- |
| Organizational | The [Summary dashboard](../operate/windows-autopatch-groups-windows-quality-update-summary-dashboard.md) provide the current update status summary for all devices.<p>The [Quality update status report](../operate/windows-autopatch-groups-windows-quality-update-status-report.md) provides the current update status of all devices at the device level. |
| Device trends | The [Quality update trending report](../operate/windows-autopatch-groups-windows-quality-update-trending-report.md) provides the update status trend of all devices over the last 90 days. |

## Windows feature update reports

The Windows feature update reports monitor the health and activity of your deployments and help you understand if your devices are maintaining update compliance targets.

If update deployments aren't successful, Windows Autopatch provides information on update deployment failures and who needs to remediate. Certain update deployment failures might require either Windows Autopatch to act on your behalf or you to fix the issue.

The Windows feature update report types are organized into the following focus areas:

| Focus area | Description |
| ----- | ----- |
| Organizational | The [Summary dashboard](../operate/windows-autopatch-groups-windows-feature-update-summary-dashboard.md) provides a broader view of the current Windows OS upgrade status for all devices registered with Windows Autopatch. |
| Operational | The [Feature update status report](../operate/windows-autopatch-groups-windows-feature-update-status-report.md) provides a per device view of the current Windows OS update status for all devices registered with Windows Autopatch. |
| Device trends | The [Quality update trending report](../operate/windows-autopatch-groups-windows-feature-update-trending-report.md) provides a visual representation of Windows OS upgrade trends for all devices over the last 90 days. |

## Who can access the reports?

Users with the following permissions can access the reports:

- Intune Service Administrator
- Global Reader
- Services Support Administrator
- Policy and Profile Manager
- Read Only Operator
- Help Desk Operator

## About data latency

The data source for these reports is Windows [diagnostic data](../overview/windows-autopatch-privacy.md#microsoft-windows-1011-diagnostic-data) and Microsoft Intune.The data typically uploads from enrolled devices every hour. Then, the data is processed in batches before being made available in Windows Autopatch. The maximum end-to-end latency is approximately four hours.



## Windows quality and feature update statuses

The following statuses are used throughout the Windows Autopatch reporting suite to describe the quality update status for devices:

- [Up to Date devices](#up-to-date-devices)
- [Not up to Date devices](#not-up-to-date-devices)
- [Not Ready devices](#not-ready-devices)

Each status has its own set of sub statuses to further describe the status.

### Up to Date devices

Up to date devices are devices that meet all of the following prerequisites:

- [Prerequisites](../prepare/windows-autopatch-prerequisites.md)
- [Prerequisites for device registration](../deploy/windows-autopatch-device-registration-overview.md#prerequisites-for-device-registration)
- [Windows quality and feature update device readiness](../deploy/windows-autopatch-post-reg-readiness-checks.md)
- [Post-device readiness checks](../deploy/windows-autopatch-post-reg-readiness-checks.md)
- Applied the current monthly cumulative updates

> [!NOTE]
> Devices that are [Up to Date](#up-to-date-devices) remain with the **In Progress** status until either the current monthly cumulative update is applied, or an [alert](../operate/windows-autopatch-device-alerts.md) is received. If the device receives an alert, the device's status changes to [Not up to Date](#not-up-to-date-devices).

#### Up to Date sub statuses

| Sub status | Description |
| ----- | ----- |
| In Progress | Devices are currently installing the latest [quality update](../operate/windows-autopatch-groups-windows-quality-update-overview.md#release-schedule) or [feature update](../operate/windows-autopatch-groups-windows-feature-update-overview.md#default-release) deployed through the Windows Autopatch release schedule. |
| Paused | Devices that are currently paused due to a customer-initiated pause. For more information, see pausing and resuming a [Windows quality update](../operate/windows-autopatch-groups-windows-quality-update-overview.md#pause-and-resume-a-release) or [Windows feature update](../operate/windows-autopatch-windows-feature-update-overview.md#pause-and-resume-a-release). |

### Not up to Date devices

Not Up to Date means a device isn't up to date when the:

- Quality or feature update is out of date, or the device is on the previous update.
- The assigned update schedule elapsed and the device still didn't apply the current release.
- Device has an [alert](../operate/windows-autopatch-device-alerts.md) resulting in an error and action must be taken.

### Not Ready devices

Not Ready refers to the responsibility of the designated IT administrator to carry out the appropriate action to resolve the reported device sub status.

Within each 24-hour reporting period, devices that are Not Ready are reevaluated using the [Autopatch post-device registration readiness checks](../deploy/windows-autopatch-post-reg-readiness-checks.md).

## Data export

Select **Export devices** to export data for each report type. Only selected columns are exported.
