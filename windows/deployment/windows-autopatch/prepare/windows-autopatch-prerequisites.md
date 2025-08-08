---
title: Prerequisites
description: This article details the prerequisites needed for Windows Autopatch
ms.date: 03/31/2025
ms.service: windows-client
ms.subservice: autopatch
ms.topic: concept-article
ms.localizationpriority: medium
author: tiaraquan
ms.author: tiaraquan
manager: bpardi
ms.reviewer: hathind
ms.collection:
  - highpri
  - tier1
---

# Prerequisites

## Licenses and entitlements

Windows Autopatch is available to the following licenses:

- Microsoft 365 Business Premium (for more information on available licenses, see [Microsoft 365 licensing](https://www.microsoft.com/microsoft-365/business/compare-all-microsoft-365-business-products-b))
- Windows 10/11 Education A3 or A5 (included in Microsoft 365 A3 or A5)
- Windows 10/11 Enterprise E3 or E5 (included in Microsoft 365 F3, E3, or E5)
- Windows 10/11 Enterprise E3 or E5 VDA

### Feature entitlement

For more information about feature entitlement, see [Features and capabilities](../overview/windows-autopatch-overview.md#features-and-capabilities). Features are accessed through the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).

| Symbol | Meaning |
| --- | --- |
| :heavy_check_mark: | All features available |
| :x: | Feature not available |

#### Windows 10 and later update policy management

| Feature | Business Premium | A3+ | E3+ | F3 |
| --- | :---: | :---: | :---: | :---: |
| Releases | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
| Update rings | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
| Quality updates | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
| Feature updates | :heavy_check_mark:| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
| Driver and firmware updates | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|

#### Tenant management

| Feature | Business Premium | A3+ | E3+ | F3 |
| --- | :---: | :---: | :---: | :---: |
| Autopatch groups | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
| New feature and change management communications | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
| Release schedule and status communications | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
| Support requests | :x: | :x: | :heavy_check_mark: | :heavy_check_mark:|

#### Reporting

| Feature | Business Premium | A3+ | E3+ | F3 |
| --- | :---: | :---: | :---: | :---: |
| Intune Reports | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
| Quality updates | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
| Feature updates | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
| Device readiness | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|

## General infrastructure requirements

| Area | Prerequisite details |
| --- | --- |
| Licensing terms and conditions for products and services | For more information about licensing terms and conditions for products and services purchased through Microsoft Commercial Volume Licensing Programs, see the [Product Terms site](https://www.microsoft.com/licensing/terms/). |
| Microsoft Entra ID and Intune | Microsoft Entra ID P1 or P2 and Microsoft Intune are required.<p>Microsoft Entra ID must either be the source of authority for all user accounts, or user accounts must be synchronized from on-premises Active Directory using the latest supported version of Microsoft Entra Connect to enable Microsoft Entra hybrid join.</p><ul><li>For more information, see [Microsoft Entra Connect](/entra/identity/hybrid/connect/whatis-azure-ad-connect) and [Microsoft Entra hybrid join](/entra/identity/devices/how-to-hybrid-join)</li><li>For more information on supported Microsoft Entra Connect versions, see [Microsoft Entra Connect:Version release history](/entra/identity/hybrid/connect/reference-connect-version-history).</li></ul> |
| Connectivity | All Windows Autopatch devices require connectivity to multiple Microsoft service endpoints from the corporate network. For the full list of required IPs and URLs, see [Configure your network](../prepare/windows-autopatch-configure-network.md). |
| Device management | [Devices must be already enrolled with Microsoft Intune](/mem/intune/user-help/enroll-windows-10-device) before registering with Windows Autopatch. Intune must be set as the Mobile Device Management (MDM) authority or co-management must be turned on and enabled on the target devices.<p>At a minimum, the Windows Update, Device configuration, and Office Click-to-Run apps workloads must be set to Pilot Intune or Intune. You must also ensure that the devices you intend on bringing to Windows Autopatch are in the targeted device collection. For more information, see [co-management requirements for Windows Autopatch](#configuration-manager-co-management-requirements).</p><p>Other device management prerequisites include:</p><ul><li>Devices must be corporate-owned. Windows bring-your-own-devices (BYOD) are blocked during device registration prerequisite checks.</li><li>Devices must be managed by either Intune or Configuration Manager co-management. Devices only managed by Configuration Manager aren't supported.</li><li>Devices must be in communication with Microsoft Intune in the last 28 days. Otherwise, the devices aren't registered with Autopatch.</li><li>Devices must be connected to the internet.</li></ul><p>See [Register your devices](../deploy/windows-autopatch-register-devices.md) for more details on device prerequisites and on how the device registration process works with Windows Autopatch.</p><p>For more information on co-management, see [co-management for Windows devices](/mem/configmgr/comanage/overview).</p> |
| Data and privacy |Deployment scheduling controls are always available. However, to take advantage of the unique deployment protections tailored to your population, devices must share diagnostic data with Microsoft. For these features, at minimum, the deployment service requires devices to send [diagnostic data](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#diagnostic-data-settings) at the Required level (previously called *Basic*) for these features.<ul><li>Optional level (previously Full) for Windows 11 devices</li><li>Enhanced level for Windows 10 devices</li></ul><p>For more information on Windows Autopatch privacy practices, see [Windows Autopatch Privacy](../overview/windows-autopatch-privacy.md).</p> |

## Windows editions, build version, and architecture

The following Windows editions, build version, and architecture **applies if you have**:

- Business Premium, A3+, E3+ or F3 licenses
- [Registered devices with Windows Autopatch](../deploy/windows-autopatch-register-devices.md)

The following Windows 10/11 editions, build version, and architecture are supported when [devices are registered with Windows Autopatch](../deploy/windows-autopatch-register-devices.md):

- Windows 11 Professional, Education, Enterprise, Pro Education, or Pro for Workstations editions
- Windows 11 IoT Enterprise edition
- Windows 10 Professional, Education, Enterprise, Pro Education, or Pro for Workstations editions
- Windows 10 IoT Enterprise edition

Windows Autopatch service supports Windows client devices on the **General Availability Channel**.

> [!IMPORTANT]
> Windows Autopatch supports registering [Windows 10 and Windows 11 Long-Term Servicing Channel (LTSC)](/windows/whats-new/ltsc/overview) devices that are being currently serviced by the [Windows 10 LTSC](/windows/release-health/release-information) or [Windows 11 LTSC](/windows/release-health/windows11-release-information). The service only supports managing the [Windows quality updates](../operate/windows-autopatch-windows-quality-update-overview.md) workload for devices currently serviced by the LTSC. Windows Update client policies and Windows Autopatch don't offer Windows feature updates for devices that are part of the LTSC. You must either use [LTSC media](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise) or the [Configuration Manager Operating System Deployment capabilities to perform an in-place upgrade](/windows/deployment/deploy-windows-cm/upgrade-to-windows-10-with-configuration-manager) for Windows devices that are part of the LTSC.

## Configuration Manager co-management requirements

The following Windows editions, build version, and architecture **applies if you have**:

- Business Premium, A3+, E3+ or F3 licenses
- [Registered devices with Windows Autopatch](../deploy/windows-autopatch-register-devices.md)

| Requirement | Description |
| --- | --- |
| Supported Configuration Manager version | Use a currently supported [Configuration Manager version](/mem/configmgr/core/servers/manage/updates#supported-versions). |
| Configuration Manager must be [cloud-attached with Intune (co-management)](/mem/configmgr/cloud-attach/overview) | Must have the following co-management workloads enabled and set to either **Intune** or **Pilot Intune**:<ul><li>Windows Update policies workload</li><li>Device configuration workload</li><li>Office Click-to-Run apps workload</li></ul><p>If you’re using **Pilot Intune**, in the **Staging** tab, the device must be in the collections that correspond to the three workloads that Windows Autopatch requires.<ul><li>If you selected Intune for one workload and Pilot Intune for the other two workloads, your devices only need to be in the two Pilot Intune collections.</li><li>If you have different collection names for each workload, your devices must be in CoMgmtPilot.</li></ul><p>**You or your Configuration Manager administrator are responsible for adding your Autopatch devices to these collections. Windows Autopatch doesn’t change or add to these collections.**</p><p>For more information, see [paths to co-management](/mem/configmgr/comanage/quickstart-paths).</p> |
| Create a Custom client setting |Create a Custom client setting in Configuration Manager to disable the Software Updates agent for Intune/Pilot Intune co-managed devices.<ol><li>Under **Disable Software Updates > Device Settings > Enable software updates on clients**, select **No**.</li><li>Under **CoMgmtSettingsProd Properties > Staging tab > Office Click-to-Run apps, set to Co-Management – O365 Workload**.</li><li>Under **CoMgmtSettingsProd Properties > Staging tab > Windows Update policies, set to Co-Management – WUfB Workload**.</li><li>Ensure the **Disable Software Updates** setting has a lower priority than your default client settings and target your co-management collection.<ol><li>If the co-management workload is set to Intune, deploy the Client Setting to a collection that includes all co-management devices, for example, Co-management Eligible Devices.</li></ol><li>Configuration Manager **disables** the Software Updates agent in the next policy cycle. However, because the Software Updates Scan Cycle is **removed**, Configuration Manager might not remove the Windows Server Update Service (WSUS) registry keys.</li><ol><li>Remove the registry values under **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate** because Windows Update client policies control the process.</li></ol></ol> |

## Required Intune permissions

For more information on roles and permissions, see [Role-based access control](../prepare/windows-autopatch-role-based-access-control.md) in Windows Autopatch.
