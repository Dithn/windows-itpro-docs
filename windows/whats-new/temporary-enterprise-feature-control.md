---
title: Enterprise feature control in Windows 11
description: Learn about the Windows 11 features behind temporary enterprise feature control and permanent feature control.
ms.service: windows-client
ms.subservice: itpro-fundamentals
ms.author: mstewart
author: mestew
manager: bpardi
ms.localizationpriority: medium
ms.topic: reference
ms.date: 08/04/2025
ms.collection:
  - highpri
  - tier2
appliesto:
  - ✅ <a href="https://learn.microsoft.com/windows/release-health/supported-versions-windows-client" target="_blank">Windows 11, version 22H2 and later</a>
---

# Enterprise feature control in Windows 11
<!--7790977-->
New features and enhancements are introduced through the monthly cumulative update to provide continuous innovation for Windows 11. To give organizations time to plan and prepare, some of these new features might be:

- Temporarily turned off by default using [temporary enterprise feature control](#temporary-enterprise-feature-control)
- Controlled by a policy that allows for [permanent enterprise feature control](#permanent-enterprise-feature-control)

Features that are turned off by default are listed in the KB article for the monthly cumulative update. Typically, a feature is selected to be off by default because it either impacts the user experience or IT administrators significantly. For example, a feature might be turned off by default if it requires a change in user behavior or if it requires IT administrators to take action before the feature can be used.


[!INCLUDE [Windows roadmap](./includes/windows-roadmap.md)]

## Temporary enterprise feature control

Features behind temporary enterprise control are automatically disabled for devices that have their Windows updates managed by policies.

### Enable features behind temporary enterprise feature control

Features that are behind temporary enterprise control will be enabled when one of the following conditions is met:

- The device installs the annual feature update that enables the new features by default
- The device receives a policy that enables features behind temporary enterprise control
  - When the policy is enabled, all features on the device behind temporary control are turned on when the device restarts.

### Policy settings for temporary enterprise feature control

You can use a policy to enable features that are behind temporary enterprise feature control. When this policy is enabled, all features that were disabled behind temporary enterprise feature control are turned on when the device reboots. The following policies apply to Windows 11, version 22H2 with [KB5022845](https://support.microsoft.com/kb/5022845) and later:

- **Group Policy:** Computer Configuration\Administrative Templates\Windows Components\Windows Update\Manage end user experience\\**Enable features introduced via servicing that are off by default**

- **CSP**: ./Device/Vendor/MSFT/Policy/Config/Update/[AllowTemporaryEnterpriseFeatureControl](/windows/client-management/mdm/policy-csp-update?toc=/windows/deployment/toc.json&bc=/windows/deployment/breadcrumb/toc.json#allowtemporaryenterprisefeaturecontrol)
   - In the Intune [settings catalog](/mem/intune/configuration/settings-catalog), this setting is named **Allow Temporary Enterprise Feature Control** under the **Windows Update for Business** category.

### Windows 11 features behind temporary enterprise feature control

The following features are behind temporary enterprise control in Windows 11:

| Feature | KB article where the feature was introduced | Feature update that ends temporary control | Notes |
|---|---|---|---|
| Agent in Windows Settings <!--10408076--> | [July 22, 2025 - KB5062660](https://support.microsoft.com/kb/5062660) | | This feature also has a permanent control. For more information, see [Configure the agent in Windows Settings](/windows/configuration/settings/agent). |
| Improved Windows search <!--9887454-->|[April 25, 2025 - KB5055627](https://support.microsoft.com/kb/5055627) |  |  Improved Windows search will continue to respect your existing [search policies](/windows/client-management/mdm/policy-csp-search). |
| Click to Do <!--9887454-->| [April 25, 2025 - KB5055627](https://support.microsoft.com/kb/5055627)| | This feature also has a permanent control. For more information, see [Manage Click to Do](/windows/client-management/manage-click-to-do). |
| Touch-optimized taskbar for 2-in-1 devices <!--8092554, WIP.25197--> | [February 28, 2023 - KB5022913](https://support.microsoft.com/kb/5022913) | [Feature Update to Windows 11, version 23H2](https://support.microsoft.com/kb/5027397) | |
| Selecting **Uninstall** for a Win32 app from the right-click menu uses the **Installed Apps** page in **Settings** rather than **Programs and Features** under the **Control Panel** <!--8092554, WIP.25300-->| [September 2023 - KB5030310](https://support.microsoft.com/kb/5030310) | [Feature Update to Windows 11, version 23H2](https://support.microsoft.com/kb/5027397) | |
| Windows Spotlight provides a minimized experience, opportunities to learn more about each image, and allows users to preview images at full screen.<!--8092554, WIP.23511 & WIP.25281, AllowWindowsSpotlight-->| [September 2023 - KB5030310](https://support.microsoft.com/kb/5030310) | [Feature Update to Windows 11, version 23H2](https://support.microsoft.com/kb/5027397) | This feature also has a permanent control. For more information, see [AllowWindowsSpotlight](/windows/client-management/mdm/policy-csp-experience#allowwindowsspotlight). |
| Copilot in Windows <!--8092554, WIP.23493 -->| [September 2023 - KB5030310](https://support.microsoft.com/kb/5030310) | [Feature Update to Windows 11, version 23H2](https://support.microsoft.com/kb/5027397) | This feature also has a permanent control. For more information, see [TurnOffWindowsCopilot](/windows/client-management/mdm/policy-csp-windowsai#turnoffwindowscopilot). |
| Dev Home <!--8092554, WIP.23506-->| [September 2023 - KB5030310](https://support.microsoft.com/kb/5030310) | [Feature Update to Windows 11, version 23H2](https://support.microsoft.com/kb/5027397) | `Get-AppxPackage -Name Microsoft.Windows.DevHome` |
| Dev Drive <!--8092554, WIP.23466-->| [September 2023 - KB5030310](https://support.microsoft.com/kb/5030310) | [Feature Update to Windows 11, version 23H2](https://support.microsoft.com/kb/5027397) | This feature also has multiple permanent control. For more information, see [EnableDevDrive](/windows/client-management/mdm/policy-csp-filesystem#enabledevdrive) and [DevDriveAttachPolicy](/windows/client-management/mdm/policy-csp-filesystem#devdriveattachpolicy). |

## Permanent enterprise feature control

New features and enhancements used to be introduced only in feature updates. However, with continuous innovation for Windows 11, new features are introduced more frequently through the monthly cumulative update. Some new features can be controlled through policies that enable you to configure them for your organization. When a feature can be controlled by a policy, it has permanent enterprise feature control.

For example, the following policy to configure search on the taskbar is a permanent enterprise feature control:

- **Group Policy:** Computer Configuration\Administrative Templates\Windows Components\Search\\**Configures search on the taskbar**

- **CSP**: ./Device/Vendor/MSFT/Policy/Config/Search/[ConfigureSearchOnTaskbarMode](/windows/client-management/mdm/policy-csp-search#configuresearchontaskbarmode)

