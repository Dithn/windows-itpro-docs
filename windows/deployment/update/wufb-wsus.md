---
title: Use Windows Update client policies and Windows Server Update Services (WSUS) together
description: Learn how to use Windows Update client policies and WSUS together using the new scan source policy.
ms.service: windows-client
ms.subservice: itpro-updates
ms.topic: how-to
author: mestew
ms.author: mstewart
manager: bpardi
ms.localizationpriority: medium
appliesto:
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 11</a>
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 10</a>
ms.date: 04/01/2025
---

# Use Windows Update client policies and WSUS together

> **Looking for consumer information?** See [Windows Update: FAQ](https://support.microsoft.com/windows/windows-update-faq-8a903416-6f45-0718-f5c7-375e92dddeb2).

The Windows update scan source policy enables you to choose what types of updates to get from either [WSUS](waas-manage-updates-wsus.md) or Windows Update client policies.

We added the scan source policy starting with the [September 1, 2021—KB5005101 (OS Builds 19041.1202, 19042.1202, and 19043.1202) Preview](https://support.microsoft.com/help/5005101) update and it applies to Window 10, version 2004 and above and Windows 11. This policy changes the way devices determine whether to scan against a local WSUS server or Windows Update service.

> [!IMPORTANT]
> - If you use Configuration Manager and have co-managed devices, see [Integrate with Windows Update client policies](/intune/configmgr/sum/deploy-use/integrate-windows-update-for-business-windows-10) for more information about configuring clients.
> - The policy **Do not allow update deferral policies to cause scans against Windows Update**, also known as Dual Scan, is no longer supported on Windows 11 and on Windows 10 it's replaced by the new Windows scan source policy and isn't recommended for use. If you configure both on Windows 10, you won't get updates from Windows Update.


## About the scan source policy

The specify scan source policy enables you to specify whether your device gets the following Windows update types form WSUS **or** from Windows Update:

- Feature updates
- Windows quality updates
- Driver and firmware updates
- Updates for other Microsoft products

We recommend using this policy on your transition from fully on-premises managed environment to a cloud supported one. Whether you move only drivers to the cloud today or drivers and quality updates and then later move your other workloads, taking a step-by-step approach might ease the transition.

## Default scan behavior

To help you better understand the scan source policy, see the following default scan behavior and how we can change it:

- If no policies are configured: All of your updates come from Windows Update.
- If you configure only the WSUS server policy:

  - On Windows 10: All of your updates come from WSUS.
  - On Windows 11: All of your updates still come from WSUS unless you configure the specify scan source policy.

- If you configure a WSUS server and deferral policies on Windows 10: All of your updates will come from Windows Update unless you specify the scan source policy or have disabled dual scan.
- If you configure a WSUS server and the scan source policy: All of your updates will come from the source chosen in the scan source policy.

> [!TIP]
> The only two relevant policies for where your updates come from are the specify scan source policy and whether or not you have configured a WSUS server. This should simplify the configuration options.

> [!NOTE]
> If you have devices configured for WSUS and don't configure the scan source policy for feature updates to come from Windows update or set any offering policies by using Windows Update client policies, then users who select "Check online for updates" on the Settings page may see the optional upgrade to Windows 11. We recommend configuring the scan source policy or an offering policy to prevent such.

## Configure the scan sources

The policy can be configured using the following two methods:

1. Group Policy: Specify source service for specific classes of Windows Updates

   - Path: Computer Configuration\Administrative Templates\Windows Components\Windows Update\Manage updates offered from Windows Server Update Service\

   :::image type="content" source="media/specify-update-type-sources.png" alt-text="Screenshot of the Group Policy for specifiying sources for update types":::

2. Configuration Service Provider (CSP) Policies: **SetPolicyDrivenUpdateSourceFor&lt;Update Type>**:

   > [!NOTE]
   > - You should configure **all** of these policies if you're using CSPs.
   > - Editing the registry to change the behavior of update policies isn't recommended. Use Group Policy or the Configuration Service Provider (CSP) policy instead of directly writing to the registry. However, if you choose to edit the registry, ensure you've configured the `UseUpdateClassPolicySource` registry key too, or the scan source won't be altered.
   > - If you're also using the **Specify settings for optional component installation and component repair** policy to enable content for FoDs and language packs, see [How to make Features on Demand and language packs available when you're using WSUS or Configuration Manager](fod-and-lang-packs.md) to verify your policy configuration.

   - [Update/SetPolicyDrivenUpdateSourceForDriverUpdates](/windows/client-management/mdm/policy-csp-update#update-setpolicydrivenupdatesourcefordriver)
   - [Update/SetPolicyDrivenUpdateSourceForFeatureUpdates](/windows/client-management/mdm/policy-csp-update#update-setpolicydrivenupdatesourceforfeature)
   - [Update/SetPolicyDrivenUpdateSourceForOtherUpdates](/windows/client-management/mdm/policy-csp-update#update-setpolicydrivenupdatesourceforother)
   - [Update/SetPolicyDrivenUpdateSourceForQualityUpdates](/windows/client-management/mdm/policy-csp-update#update-setpolicydrivenupdatesourceforquality)
