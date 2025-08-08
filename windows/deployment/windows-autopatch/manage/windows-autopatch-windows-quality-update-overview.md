---
title: Windows quality updates overview
description: This article explains how Windows quality updates are managed
ms.date: 03/31/2025
ms.service: windows-client
ms.subservice: autopatch
ms.topic: article
ms.localizationpriority: medium
author: tiaraquan
ms.author: tiaraquan
manager: bpardi
ms.reviewer: andredm7
ms.collection:
  - highpri
  - tier1
---

# Windows quality updates

You can manage Windows quality update profiles for Windows 10 and later devices. You can expedite a specific Windows quality update using targeted policies.

For more information about how to expedite quality update for Windows 10 or later in Microsoft Intune, see [Use Intune to expedite Windows quality updates](/mem/intune/protect/windows-10-expedite-updates).

## Service level objective

Windows Autopatch aims to keep at least 95% of [Up to Date devices](../monitor/windows-autopatch-windows-quality-and-feature-update-reports-overview.md#up-to-date-devices) on the latest quality update. Autopatch uses the previously defined release schedule on a per ring basis with a five-day reporting period to calculate and evaluate the service level objective (SLO). The result of the service level objective is the column "% with the latest quality update" displayed in the Windows updates blade and reporting.

## Service level objective calculation

There are two states a device can be in when calculating the service level objective (SLO):

- Devices that are active during the release
- Devices that become active after the release

The service level objective for each of these states is calculated as:

| State | Calculation |
| ----- | ----- |
| Device that is active during release | This service level objective calculation assumes the device has typical activity during the scheduled release period. Calculated by:<p>`Deferral + Deadline + Reporting Period = service level objective`</p> |
| Device that becomes active after release | This service level objective calculation refers to offline devices during the scheduled release period but come back online later. Calculated by:<p>`Grace Period + Reporting period = service level objective`</p> |

| Timeframe | Value defined in |
| ----- | ----- |
| Deferral | Targeted deployment ring |
| Deadline | Targeted deployment ring |
| Grace period | Targeted deployment ring |
| Reporting period | Five days. Value defined by Windows Autopatch. |

> [!NOTE]
> Targeted deployment ring refers to the deployment ring value of the device in question. If a device has a five day deferral with a two day deadline, and two day grace period, the SLO for the device would be calculated to `5 + 2 + 5 = 12`-day service level objective from the second Tuesday of the month. The five day reporting period is one established by Windows Autopatch to allow enough time for device check-in reporting and data evaluation within the service.

> [!IMPORTANT]
> Windows Autopatch supports registering [Windows 10 and Windows 11 Long-Term Servicing Channel (LTSC)](/windows/whats-new/ltsc/overview) devices that are being currently serviced by the [Windows 10 LTSC](/windows/release-health/release-information) or [Windows 11 LTSC](/windows/release-health/windows11-release-information). The service only supports managing the [Windows quality updates](../operate/windows-autopatch-windows-quality-update-overview.md) workload for devices currently serviced by the LTSC. Windows Update client policies and Windows Autopatch don't offer Windows feature updates for devices that are part of the LTSC. You must either use [LTSC media](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise) or the [Configuration Manager Operating System Deployment capabilities to perform an in-place upgrade](/windows/deployment/deploy-windows-cm/upgrade-to-windows-10-with-configuration-manager) for Windows devices that are part of the LTSC.

## Pause and resume a release

> [!IMPORTANT]
> **Pausing or resuming an update can take up to eight hours to be applied to devices**. Windows Autopatch uses Microsoft Intune as its device management solution and that's the average frequency Windows devices take to communicate back to Microsoft Intune with new instructions to pause, resume or rollback updates.
>
> For more information, see [how long does it take for devices to get a policy, profile, or app after they are assigned from Microsoft Intune](/intune/intune-service/configuration/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

**To pause and resume a release:**

> [!NOTE]
> If you pause an update, the specified release has the **Paused** status. You must select **Resume** to resume the update.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Select **Devices** from the left navigation menu.
1. Under the **Manage updates** section, select **Windows updates**.
1. In the **Windows updates** blade, select the **Update rings** tab.
1. Select the Autopatch group or deployment ring that you want to pause or resume. Select either: **Pause** or **Resume**. Alternatively, you can select the **horizontal ellipses (...)** of the Autopatch group or deployment ring you want to pause or resume. Select, **Pause**, or **Resume** from the dropdown menu.
1. If you're resuming an update, you can select one or more Autopatch groups or deployment rings.
1. Select **Pause or Resume deployment**.

## Remediating Not ready and/or Not up to Date devices

To ensure your devices receive Windows quality updates, Windows Autopatch provides information on how you can [remediate Windows Autopatch device alerts](../monitor/windows-autopatch-device-alerts.md).
