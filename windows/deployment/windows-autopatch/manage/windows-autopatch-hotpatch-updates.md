---
title: Hotpatch updates
description: Use Hotpatch updates to receive security updates without restarting your device
ms.date: 07/04/2025
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

# Hotpatch updates

With hotpatch updates, you can quickly take measures to help protect your organization from the evolving landscape of cyberattacks, while minimizing user disruptions. Hotpatch updates are [Monthly B release security updates](/windows/deployment/update/release-cycle#monthly-security-update-release) that install and take effect without requiring you to restart the device. By minimizing the need to restart, these updates help ensure faster compliance, making it easier for organizations to maintain security while keeping workflows uninterrupted.

Hotpatch is an extension of Windows Update and requires Autopatch to create and deploy hotpatches to devices enrolled in the Autopatch quality update policy.

## Key benefits

- Hotpatch updates streamline the installation process and enhance compliance efficiency.
- No changes are required to your existing update ring configurations. Your existing ring configurations are honored alongside Hotpatch policies.
- The [Hotpatch quality update report](../monitor/windows-autopatch-hotpatch-quality-update-report.md) provides a per policy level view of the current update statuses for all devices that receive Hotpatch updates.

## Prerequisites

To benefit from Hotpatch updates, devices must meet the following prerequisites:

- One of the eligible licenses: Windows 11 Enterprise E3 or E5, Microsoft 365 F3, Windows 11 Education A3 or A5, Microsoft 365 Business Premium, or Windows 365 Enterprise  
- Windows 11 Enterprise version 24H2 or later
- Devices must be on the latest baseline release version to qualify for Hotpatch updates. Microsoft releases Baseline updates quarterly as standard cumulative updates. For more information on the latest schedule for these releases, see [Release notes for Hotpatch](https://support.microsoft.com/topic/release-notes-for-hotpatch-in-azure-automanage-for-windows-server-2022-4e234525-5bd5-4171-9886-b475dabe0ce8?preview=true).
- Microsoft Intune to manage hotpatch update deployment with the [Windows quality update policy with hotpatch turned on](#enroll-devices-to-receive-hotpatch-updates).

## Operating system configuration prerequisites

To prepare a device to receive Hotpatch updates, configure the following operating system settings on the device. You must configure these settings for the device to be offered the Hotpatch update and to apply all Hotpatch updates.

### Virtualization based security (VBS)

VBS must be turned on for a device to be offered Hotpatch updates. For information on how to set and detect if VBS is enabled, see [Virtualization-based Security (VBS)](/windows/security/hardware-security/enable-virtualization-based-protection-of-code-integrity?tabs=security).

> [!NOTE]
> Devices might be temporarily ineligible because they don’t have VBS enabled or aren’t currently on the latest baseline release. To ensure that all your Windows devices are configured properly to be eligible for hotpatch updates, see [Troubleshoot hotpatch updates](#troubleshoot-hotpatch-updates).

### Arm 64 devices must disable compiled hybrid PE usage (CHPE) (Arm 64 CPU Only)

> [!NOTE]
> **Hotpatch updates on Arm 64 devices follow the same [release cycle](#release-cycles).**

This requirement only applies to Arm 64 CPU devices when using Hotpatch updates. Hotpatch updates aren't compatible with servicing CHPE OS binaries located in the `%SystemRoot%\SyChpe32` folder.

To ensure all the Hotpatch updates are applied, you must set the CHPE disable flag and restart the device to disable CHPE usage. You only need to set this flag one time. The registry setting remains applied through updates.

> [!IMPORTANT]
> This setting is required because it forces the operating system to use the emulation x86-only binaries instead of CHPE binaries on Arm 64 devices. CHPE binaries include native Arm 64 code to improve performance, excluding the CHPE binaries might affect performance or compatibility. Be sure to test application compatibility and performance before rolling out Hotpatch updates widely on Arm 64 CPU based devices.

To disable CHPE, create and/or set the following DWORD registry key:
Path: `HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management`
DWORD key value: HotPatchRestrictions=1

You can also use the CSP DisableCHPE. For more information, see [DisableCHPE](/windows/client-management/mdm/policy-csp-system#disablechpe).

> [!NOTE]
> There are no plans to support hotpatch updates on Arm64 devices with CHPE enabled. Disabling CHPE is required only for Arm64 devices. AMD and Intel CPUs don’t have CHPE.

If you choose to no longer use Hotpatch updates, clear the CHPE disable flag (`HotPatchRestrictions=0`) then restart the device to turn on CHPE usage.

## Ineligible devices

Devices that don't meet one or more prerequisites automatically receive the Latest Cumulative Update (LCU) instead. Latest Cumulative Update (LCU) contains monthly updates that supersede the previous month's updates containing both security and nonsecurity releases.

LCUs requires you to restart the device, but the LCU ensures that the device remains fully secure and compliant.

> [!NOTE]
> If devices aren't eligible for Hotpatch updates, these devices are offered the LCU. The LCU keeps your configured Update ring settings, it doesn't change the settings.

## Release cycles

For more information about the release calendar for hotpatch updates, see [Release notes for Hotpatch](https://support.microsoft.com/topic/release-notes-for-hotpatch-public-preview-on-windows-11-version-24h2-enterprise-clients-c117ee02-fd35-4612-8ea9-949c5d0ba6d1).

- Baseline: Includes the latest security fixes, cumulative new features, and enhancements. Restart required.
- Hotpatch: Includes security updates. No restarted required.

| Quarter | Baseline updates (requires restart) | Hotpatch (no restart required) |
| ----- | ----- | ----- |
| 1 | January | February and March |
| 2 | April | May and June |
| 3 | July | August and September |
| 4 | October | November and December |

## Hotpatch on Windows 11 Enterprise or Windows Server 2025

> [!NOTE]
> Hotpatch is also available on Windows Server and Windows 365. For more information, see [Hotpatch for Windows Server Azure Edition](/windows-server/get-started/enable-hotpatch-azure-edition).

Hotpatch updates are similar between Windows 11 and Windows Server 2025.

- Windows Autopatch manages Windows 11 updates
- Azure Update Manager and optional Azure Arc subscription for Windows 2025 Datacenter/Standard Editions (on-premises) manages Windows Server 2025 Datacenter Azure Edition. For more information, on Windows Server and Windows 365, see [Hotpatch for Windows Server Azure Edition](/windows-server/get-started/enable-hotpatch-azure-edition).

The calendar dates, eight hotpatch months, and four baseline months, planned each year are the same for all the hotpatch-supported operating systems (OS). It’s possible for additional baseline months for one OS (for example, Windows Server 2022), while there are hotpatch months for another OS, such as Server 2025 or Windows 11, version 24H2. Review the release notes from [Windows release health](/windows/release-health/) to keep up to date.

## Enroll devices to receive Hotpatch updates

> [!NOTE]
> If you're using Autopatch groups and want your devices to receive Hotpatch updates, you must create a Hotpatch policy and assign devices to it. Turning on Hotpatch updates doesn't change the deferral setting applied to devices within an Autopatch group.

**To enroll devices to receive Hotpatch updates:**

1. Go to the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
1. Select **Devices** from the left navigation menu.
1. Under the **Manage updates** section, select **Windows updates**.
1. Go to the **Quality updates** tab.
1. Select **Create**, and select **Windows quality update policy**.
1. Under the **Basics** section, enter a name for your new policy and select Next.
1. Under the **Settings** section, ensure that the option **"When available, apply without restarting the device ("Hotpatch")** is set to **Allow**. Then, select **Next**.
1. Select the appropriate Scope tags or leave as Default. Then, select **Next**.
1. Assign the devices to the policy and select **Next**.
1. Review the policy and select **Create**.
2. You can also **Edit** the existing **Windows quality update policy** and set the **"When available, apply without restarting the device ("Hotpatch")** to **Allow**.

These steps ensure that targeted devices, which are [eligible](#prerequisites) to receive Hotpatch updates, are configured properly. [Ineligible devices](#ineligible-devices) are offered the latest cumulative updates (LCU).

> [!NOTE]
> Turning on Hotpatch updates doesn't change the existing deadline-driven or scheduled install configurations on your managed devices. Deferral and active hour settings still apply.

## Roll back a hotpatch update

Automatic rollback of a Hotpatch update isn’t supported but you can uninstall them. If you experience an unexpected issue with hotpatch updates, you can investigate by uninstalling the hotpatch update and installing the latest standard cumulative update (LCU) and restart. Uninstalling a hotpatch update is quick, however, it does require a device restart.

## Troubleshoot hotpatch updates

### Step 1: Verify the device is eligible for hotpatch updates and on a hotpatch baseline before the hotpatch update is installed

Hotpatching follows the hotpatch release cycle. Review the prerequisites to ensure the device is [eligible](#prerequisites) for hotpatch updates. For information on devices that don’t meet the prerequisites, see [Ineligible devices](#ineligible-devices).

For the latest release schedule, see the [hotpatch release notes](https://support.microsoft.com/topic/release-notes-for-hotpatch-public-preview-on-windows-11-version-24h2-enterprise-clients-c117ee02-fd35-4612-8ea9-949c5d0ba6d1). For information on Windows update history, see [Windows 11, version 24H2 update history](https://support.microsoft.com/topic/windows-11-version-24h2-update-history-0929c747-1815-4543-8461-0160d16f15e5).

### Step 2: Verify the device has Virtualization-based security (VBS) turned on

1. Select **Start**, and enter `System information` in the Search.
1. Select **System information** from the results.
1. Under **System summary**, under the **Item column**, find **Virtualization-based security**.
1. Under the **Value column**, ensure it states **Running**.

### Step 3: Verify the device is properly configured to turn on hotpatch updates

1. In Intune, review your configured policies within Autopatch to see which groups of devices are targeted with a hotpatch policy by going to the **Windows Update** > **Quality Updates** page.
1. Ensure the hotpatch update policy is set to **Allow**.
1. On the device, select **Start** > **Settings** > **Windows Update** > **Advanced options** > **Configured update policies** > find **Enable hotpatching when available**. This setting indicates that the device is enrolled in hotpatch updates as configured by Autopatch.

### Step 4: Disable compiled hybrid PE usage (CHPE) (Arm64 CPU only)

For more information, see [Arm 64 devices must disable compiled hybrid PE usage (CHPE) (Arm 64 CPU Only)](#arm-64-devices-must-disable-compiled-hybrid-pe-usage-chpe-arm-64-cpu-only).

### Step 5: Use Event viewer to verify the device has hotpatch updates turned on

1. Right-click on the **Start** menu, and select **Event viewer**.
1. Search for **AllowRebootlessUpdates** in the filter. If AllowRebootlessUpdates is set to `1`, the device is enrolled in the Autopatch update policy and has hotpatch updates turned on:

``
"data": {
"payload": "{\"Orchestrator\":{\"UpdatePolicy\":{\"Update/AllowRebootlessUpdates\":true}}}",
"isEnrolled": 1,
"isCached": 1,
"vbsState": 2,
``

### Step 6: Check Windows Logs for any hotpatch errors

Hotpatch updates provide an inbox monitor service that checks for the health of the updates installed on the device. If the monitor service detects an error, the service logs an event in the Windows Application Logs. If there's a critical error, the device installs the standard (LCU) update to ensure the device is fully secure.

1. Right-click on the **Start** menu, and select **Event viewer**.
1. Search for **hotpatch** in the filter to view the logs.
