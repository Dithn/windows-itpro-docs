---
title: Hotpatch quality update report
description: Use the Hotpatch quality update report to view the current update statuses for all devices that receive Hotpatch updates
ms.date: 04/04/2025
ms.service: windows-client
ms.subservice: autopatch
ms.topic: how-to
ms.localizationpriority: medium
author: tiaraquan
ms.author: tiaraquan
manager: bpardi
ms.reviewer: adnich
ms.collection:
  - highpri
  - tier1
---

# Hotpatch quality update report

The Hotpatch quality update report provides a per policy level view of the current update statuses for all devices that receive Hotpatch updates. For more information about Hotpatching, see [Hotpatch updates](../manage/windows-autopatch-hotpatch-updates.md).

**To view the Hotpatch quality update status report:**

1. Go to the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Navigate to **Reports** > **Windows Autopatch** > **Windows quality updates**.
1. Select the **Reports** tab.
1. Select **Hotpatch quality updates**.

> [!NOTE]
> The data in this report is refreshed every four hours with data received by your Windows Autopatch managed devices. The last refreshed on date/time can be seen at the top of the page. For more information about how often Windows Autopatch receives data from your managed devices, see [Data latency](../monitor/windows-autopatch-windows-quality-and-feature-update-reports-overview.md#about-data-latency).

## Report information

The Hotpatch quality update report provides a visual representation of the update status trend for all devices over the last 90 days.

### Default columns

The following information is available as default columns in the Hotpatch quality update report:

| Column name | Description |
| ----- | ----- |
| Quality update policy | The name of the policy. |
| Device name | Total number of devices in the policy. |
| Up to date | Total device count reporting a status of Up to date. For more information, see [Up to Date](../operate/windows-autopatch-groups-windows-quality-and-feature-update-reports-overview.md#up-to-date-devices). |
| Hotpatched | Total devices that successfully received a Hotpatch update. |
| Not up to Date | Total device count reporting a status of Not Up to date. For more information, see [Not Up to Date](../operate/windows-autopatch-groups-windows-quality-and-feature-update-reports-overview.md#not-up-to-date-devices). |
| In progress | Total device counts reporting the In progress status. For more information, see [In progress](../operate/windows-autopatch-groups-windows-quality-and-feature-update-reports-overview.md#up-to-date-sub-statuses). |
| % with the latest quality update | Percent of [Up to Date](../operate/windows-autopatch-groups-windows-quality-and-feature-update-reports-overview.md#up-to-date-devices) devices on the most current Windows release and its build number |
| Not ready | Total device count reporting the Not ready status. For more information, see [Not ready](../operate/windows-autopatch-groups-windows-quality-and-feature-update-reports-overview.md#not-up-to-date-devices). |
| Paused | Total device count reporting the Paused status. For more information, see [Up to Date](../operate/windows-autopatch-groups-windows-quality-and-feature-update-reports-overview.md#up-to-date-devices). |

## Report options

The following options are available:

| Option | Description |
| ----- | ----- |
| By percentage | Select **By percentage** to show your trending graphs and indicators by percentage. |
| By device count | Select **By device count** to show your trending graphs and indicators by numeric value. |
