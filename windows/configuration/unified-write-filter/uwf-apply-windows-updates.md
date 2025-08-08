---
title: Apply Windows updates to UWF-protected devices
description: Apply Windows updates to UWF-protected devices
ms.date: 05/02/2017
ms.topic: reference
---

# Apply Windows updates to UWF-protected devices

When a device is protected with Unified Write Filter (UWF), you must use UWF servicing mode commands to service the device and apply updates to an image.

UWF servicing mode uses the following files to when it applies Windows updates to your device:

- UWFMgr.exe command-line tool
- UwfServicingScr.scr screen saver
- UwfServicingMasterScript.cmd script

> [!NOTE]
> The master servicing script can be modified to service third-party applications, service custom OEM applications, or call custom OEM servicing scripts.

UWF servicing supports the following types of Windows updates:

- Critical updates
- Security updates
- Driver updates

## Enable Servicing Mode

1. To apply Windows updates to your device, at an administrator command prompt, type the following command:

   ```cmd
   uwfmgr.exe servicing enable
   ```

1. Restart the device. Use either command.

   ```cmd
   uwfmgr.exe filter restart
   ```

   ```cmd
   shutdown /r /t 0
   ```

On restart, the device automatically signs in to the servicing account and servicing starts.

> [!IMPORTANT]
> The default servicing account that is automatically created and used for servicing is named **UWF-Servicing**. It's important that you don't have a user account that has that same name on a device before starting UWF servicing.

Once servicing has started, no user interaction is required. The system may restart if it's required by the Windows updates that are installing. If a restart is required, the system reenters servicing mode on restart and continues until all updates are installed.

While servicing is underway, the UwfServicingScr.scr screen saver displays on the device.

> [!NOTE]
> The UwfServicingScr.scr screen saver that is included with Windows 10 Enterprise is a standard Windows screen saver and can be replaced by a custom OEM screen saver if necessary.

When Windows update servicing is finished, the system disables UWF servicing and restarts the system with UWF-protection enabled and all file and registry exclusions restored to their original pre-servicing state.

> [!NOTE]
> During UWF servicing in Windows 10 Enterprise, Windows Update automatically accepts all Microsoft Software License Terms.

> [!NOTE]
> If Windows updates can't be installed or return an error, servicing is disabled and the system restarts with UWF-protection re-enabled and all file and registry exclusions restored to their original pre-servicing state.

## Related articles

- [Unified Write Filter]( index.md)
- [UWF master servicing script](uwf-master-servicing-script.md)
- [UWF servicing screen saver](uwf-servicing-screen-saver.md)
