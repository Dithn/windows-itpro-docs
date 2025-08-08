---
title: Service UWF-protected devices
description: Service UWF-protected devices
ms.date: 10/02/2018
ms.topic: reference
---

# Service UWF-protected devices

To update your devices, use UWF servicing mode. UWF servicing mode allows you to apply Windows updates, anti-malware signature file updates, and custom software or third-party software updates.

Normally, when the Unified Write Filter (UWF) is active, system updates are disabled, as they would be erased when the overlay is cleared.

When UWF servicing mode is triggered, Windows does the following:

1. Clears the UWF overlay
1. Reboots the devices
1. Triggers a system maintenance hour
1. Disables the UWF filter
1. Scans for and applies Windows updates
1. Scans for and applies app updates from the Microsoft store
1. After servicing is complete, it re-enables the UWF filter and resumes UWF protection

>[!NOTE]
> Servicing mode requires that all user accounts on the system have a password. If there's a user account that doesn't include a password, UWF servicing fails.

## In this section

| Article                                     | Description                                                                        |
|:------------------------------------------|:-----------------------------------------------------------------------------------|
| [Anti-malware support on UWF-protected devices](uwf-antimalware-support.md) |Describes the procedures to add support for Microsoft Defender and System Center Endpoint Protection (SCEP/Forefront) anti-malware to your UWF-protected devices. |
| [Apply OEM updates to UWF-protected devices](uwf-apply-windows-updates.md) |Provides information about how to apply OEM updates to a UWF-protected device. |
| [Apply Windows updates to UWF-protected devices](uwf-apply-windows-updates.md) | Describes the procedures to apply Windows updates to your UWF-protected devices. |
| [UWF master servicing script](uwf-master-servicing-script.md) | Provides information about the UWF master servicing script (UwfServicingMasterScript.cmd). |
| [UWF servicing screen saver](uwf-servicing-screen-saver.md) | Provides information about how to modify the default UWF servicing screen saver. |
