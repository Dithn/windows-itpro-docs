---
title: Configure Storage Sense in Windows
description: Learn how to configure Storage Sense, a Windows feature that helps manage disk space by automatically cleaning up temporary files and unused content.
ms.topic: how-to
ms.date: 07/10/2025
author: paolomatarazzo
ms.author: paoloma
---

# Configure Storage Sense

Storage Sense is a Windows feature that helps automatically free up disk space by deleting unnecessary files—like temporary files, items in the recycle bin, and offline content from OneDrive. For IT administrators, especially those managing large device fleets, configuring Storage Sense is a low-effort, high-impact way to ensure devices remain performant and up to date. When left unmanaged, low disk space can prevent critical updates from installing, degrade system performance, and lead to user frustration. When configuring Storage Sense through policy settings, IT admins can automate storage maintenance and reduce support overhead.

## Practical scenarios

In sectors like education and in frontline roles across industries such as retail, healthcare, or manufacturing, devices with limited storage capacity are commonly deployed due to cost and portability considerations. For example, students using 64 GB Windows laptops in a shared device program might quickly run out of space due to cached files, downloads, and app data. Similarly, frontline workers using shared, shift-based devices often lack the time or permissions to manage storage manually. In both scenarios, Storage Sense can be configured to automatically remove unused files and optimize storage, helping ensure devices stay responsive and updates install without disruption.

## Configuration

By default, Storage Sense is enabled and set to run automatically when disk space is running low. IT administrators can customize its behavior to align with organizational policies and user requirements.

The available configuration options include:

- Enable or disable Storage Sense at the system level.
- Enable or disable the cleanup of user temporary files.
- Set retention thresholds for cloud-backed content: define the minimum number of days a file must remain unaccessed before it's offloaded from the local device (while remaining available in the cloud).
- Configure cleanup of the Downloads folder: specify the minimum number of days files must remain unaccessed before deletion.
- Configure cleanup of the Recycle Bin: set how many days items remain before permanent removal.
- Define the execution cadence for Storage Sense: choose to run Storage Sense daily, weekly, monthly, or only when disk space is low.

[!INCLUDE [tab-intro](../../../includes/configure/tab-intro.md)]

#### [:::image type="icon" source="../images/icons/intune.svg" border="false"::: **Intune**](#tab/intune)

[!INCLUDE [intune-settings-catalog-1](../../../includes/configure/intune-settings-catalog-1.md)]

| Category | Setting name | Value |
|--|--|--|
| **Storage** | Allow Storage Sense Global | Toggle to **Allow** or **Block** |
| **Storage** | Allow Storage Sense Temporary Files Cleanup | Toggle to **Allow** or **Block** |
| **Storage** | Config Storage Sense Cloud Content Dehydration Threshold | Specify a value in the range **0-365** |
| **Storage** | Config Storage Sense Downloads Cleanup Threshold | Specify a value in the range **0-365** |
| **Storage** | Config Storage Sense Recycle Bin Cleanup Threshold | Specify a value in the range **0-365** |
| **Storage** | Config Storage Sense Global Cadence | Choose from:<br>&nbsp;&nbsp;**0** - Only when disk space is low (default)<br>&nbsp;&nbsp;**1** - Daily<br>&nbsp;&nbsp;**7** - Weekly<br>&nbsp;&nbsp;**30** - Monthly |

[!INCLUDE [intune-settings-catalog-2](../../../includes/configure/intune-settings-catalog-2.md)]

#### [:::image type="icon" source="../images/icons/csp.svg"::: **CSP**](#tab/csp)

You can configure devices using the [Policy CSP][CSP-1].

| Setting |
|--|
|- **OMA-URI:** `./Device/Vendor/MSFT/Policy/Config/Storage/`[AllowStorageSenseGlobal](/windows/client-management/mdm/policy-csp-Storage#allowstoragesenseglobal)<br>- **Data type:** Integer<br>- **Value:**<br>&nbsp;&nbsp;`1` to allow<br>&nbsp;&nbsp;`0` to block|
|- **OMA-URI:** `./Device/Vendor/MSFT/Policy/Config/Storage/`[AllowStorageSenseTemporaryFilesCleanup](/windows/client-management/mdm/policy-csp-Storage#allowstoragesensetemporaryfilescleanup)<br>- **Data type:** Integer<br>- **Value:** <br>&nbsp;&nbsp;`1` to allow<br>&nbsp;&nbsp;`0` to block |
|- **OMA-URI:** `./Device/Vendor/MSFT/Policy/Config/Storage/`[ConfigStorageSenseCloudContentDehydrationThreshold](/windows/client-management/mdm/policy-csp-Storage#configstoragesensecloudcontentdehydrationthreshold)<br>- **Data type:** Integer<br>- **Value:** [0-365] |
|- **OMA-URI:** `./Device/Vendor/MSFT/Policy/Config/Storage/`[ConfigStorageSenseDownloadsCleanupThreshold](/windows/client-management/mdm/policy-csp-Storage#configstoragesensedownloadscleanupthreshold)<br>- **Data type:** Integer<br>- **Value:** [0-365] |
|- **OMA-URI:** `./Device/Vendor/MSFT/Policy/Config/Storage/`[ConfigStorageSenseRecycleBinCleanupThreshold](/windows/client-management/mdm/policy-csp-Storage#configstoragesenserecyclebincleanupthreshold)<br>- **Data type:** Integer<br>- **Value:** [0-365] |
|- **OMA-URI:** `./Device/Vendor/MSFT/Policy/Config/Storage/`[ConfigStorageSenseGlobalCadence](/windows/client-management/mdm/policy-csp-Storage#configstoragesenseglobalcadence)<br>- **Data type:** Integer<br>- **Value:**<br>&nbsp;&nbsp;`0` - Only when disk space is low (default)<br>&nbsp;&nbsp;`1` - Daily<br>&nbsp;&nbsp;`7` - Weekly<br>&nbsp;&nbsp;`30` - Monthly |

#### [:::image type="icon" source="../images/icons/group-policy.svg" border="false"::: **GPO**](#tab/gpo)

[!INCLUDE [gpo-settings-1](../../../includes/configure/gpo-settings-1.md)]

| Group policy path | Group policy setting | Value |
| - | - | - |
| **Computer Configuration\Administrative Templates\System\Storage Sense** | Allow Storage Sense | **Enabled** or **Disabled**|
| **Computer Configuration\Administrative Templates\System\Storage Sense** | Allow Storage Sense Temporary Files Cleanup |**Enabled** or **Disabled**|
| **Computer Configuration\Administrative Templates\System\Storage Sense** | Config Storage Sense Cloud Content Dehydration Threshold |Specify a value in the range **0-365** |
| **Computer Configuration\Administrative Templates\System\Storage Sense** | Config Storage Sense Downloads Cleanup Threshold |Specify a value in the range **0-365** |
| **Computer Configuration\Administrative Templates\System\Storage Sense** | Config Storage Sense Recycle Bin Cleanup Threshold |Specify a value in the range **0-365** |
| **Computer Configuration\Administrative Templates\System\Storage Sense** | Config Storage Sense Global Cadence | Choose from:<br>&nbsp;&nbsp;**During low free disk space** (default)<br>&nbsp;&nbsp;**Every day**<br>&nbsp;&nbsp;**Every week**<br>&nbsp;&nbsp;**Every month**|

[!INCLUDE [gpo-settings-2](../../../includes/configure/gpo-settings-2.md)]

#### [:::image type="icon" source="../images/icons/settings-app.svg"::: **Settings**](#tab/settings)

1. Go to **Settings > System > Storage > Storage Sense**, or use the following shortcut:

    > [!div class="nextstepaction"]
    >
    > [Storage Sense](ms-settings:storagepolicies)

1. Configure the following options:

    - **Cleanup of temporary files**
    - **Automatic User content cleanup**
    - **Locally available cloud content**
    - **Cleanup schedules**

---

## User Experience

When Storage Sense is configured, automatic disk space management is executed without needing to manually delete temporary files or manage storage. This leads to a smoother user experience, as devices remain responsive and updates can be installed without issues related to low disk space. Users might notice that temporary files are cleaned up periodically, and they don't have to worry about running out of space due to cached data or old files.

## Related articles

Here are some related articles that can help you learn more about managing disk space in Windows:

- [Cleanmgr][WIN-1]: The command-line utility `cleanmgr.exe`, also known as *Disk Cleanup*, shares overlapping functionalities with Storage Sense and has historically served a similar purpose. Unlike cleanmgr.exe, Storage Sense is a modern, automated disk cleanup feature introduced in Windows 10 and enhanced in later versions.
- [Shared PC feature][WIN-2]: Enables IT administrators to deliver a streamlined shared device experience. It includes capabilities such as automatic deletion of user profiles based on inactivity or disk space thresholds, and the ability to restrict access to local storage through File Explorer.
- [Delete user profiles][CSP-5]: This policy setting allows an administrator to automatically delete user profiles on system restart that haven't been used within a specified number of days.
- [FileExplorer CSP][CSP-2]: Offers settings to manage file access and visibility. Use [SetAllowedFolderLocations][CSP-3] and [SetAllowedStorageLocations][CSP-4] policy settings to restrict access to certain storage or folder locations in File Explorer, enhancing security and compliance in managed environments.

<!--links-->

[CSP-1]: /windows/client-management/mdm/policy-csp-settings#pagevisibilitylist
[CSP-2]: /windows/client-management/mdm/policy-csp-fileexplorer
[CSP-3]: /windows/client-management/mdm/policy-csp-fileexplorer#setallowedfolderlocations
[CSP-4]: /windows/client-management/mdm/policy-csp-fileexplorer#setallowedstoragelocations
[CSP-5]: /windows/client-management/mdm/policy-csp-admx-userprofiles?WT.mc_id=Portal-Microsoft_Intune_Workflows#cleanupprofiles
[INT-1]: /mem/intune/configuration/settings-catalog
[WIN-1]: /windows-server/administration/windows-commands/cleanmgr
[WIN-2]: /windows/configuration/shared-pc/shared-devices-concepts
