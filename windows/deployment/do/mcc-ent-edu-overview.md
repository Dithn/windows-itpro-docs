---
title: Microsoft Connected Cache for Enterprise and Education Overview
description: Overview, supported scenarios, and content types for Microsoft Connected Cache for Enterprise and Education.
ms.service: windows-client
ms.subservice: itpro-updates
ms.topic: article
ms.author: lichris
author: chrisjlin
manager: naengler
ms.reviewer: mstewart
ms.collection: tier3
appliesto: 
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 11</a>
- ✅ <a href=https://learn.microsoft.com/windows/deployment/do/waas-microsoft-connected-cache target=_blank>Microsoft Connected Cache for Enterprise and Education</a>	
ms.date: 07/23/2025
---

# Microsoft Connected Cache for Enterprise and Education Overview

Microsoft Connected Cache for Enterprise and Education is a software-only caching solution that facilitates delivery of Microsoft content within enterprise and education networks. Connected Cache can be managed from the Azure portal or through Azure CLI. It can be deployed to as many physical or virtual host machines as needed. Managed Windows devices can be configured to request Microsoft content from a Connected Cache host machine by applying Delivery Optimization policies using device management tools such as Microsoft Intune.

For information about Microsoft Connected Cache in Configuration Manager<!-- version 2111-->, see [Microsoft Connected Cache in Configuration Manager](/configmgr/core/plan-design/hierarchy/microsoft-connected-cache).

Microsoft Connected Cache deployed directly to Windows relies on [Windows Subsystem for Linux (WSL)](/windows/wsl/about), which runs in a user context and therefore requires either a [Group Managed Service Account](/windows-server/identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/getting-started-with-group-managed-service-accounts), local user account, or domain user account. More information about host machine prerequisites can be found in the [Microsoft Connected Cache for Enterprise and Education prerequisites](mcc-ent-prerequisites.md) article.

## Supported scenarios and configurations

Microsoft Connected Cache for Enterprise and Education supports all Windows cloud downloads that use Delivery Optimization, including the following content delivery scenarios:

- Windows Autopilot deployment scenarios
- Co-managed clients that get monthly updates and Win32 apps from Microsoft Intune
- Cloud-only managed devices, such as Intune-enrolled devices without the Configuration Manager client, that get monthly updates and Win32 apps from Microsoft Intune

Microsoft Connected Cache is built for flexible deployments to support several different enterprise configurations.

### Branch offices

Customers may have globally dispersed office sites that have some or all of the following characteristics:

- 10 to 50 Windows devices on-site
- No dedicated server hardware
- Limited internet bandwidth (satellite internet)
- Intermittent internet connectivity

To support their branch offices, customers can deploy Connected Cache to a Windows 11 client device.

### Large enterprise sites

Customers may have office spaces, datacenters, or other Azure deployments that have some or all of the following characteristics:  

- 100s or 1,000s of Windows devices (desktop or server)
- Existing server hardware (Decommissioned Distribution Point, file server, cloud print server)
- Azure VM and/or Azure Virtual Desktop deployments
- Limited internet bandwidth (T1 or T3 lines)

To support their large enterprise sites, customers can deploy Connected Cache to a server running Windows Server 2022 (or later) or Ubuntu 24.04.

See [Connected Cache node host machine requirements](mcc-ent-prerequisites.md) for recommended host machine specifications.

| Enterprise configuration | Download speed range | Download speeds and approximate content volume delivered in 8 Hours |
|---|---|---|
|Branch office|< 1 Gbps Peak| 500 Mbps => 1,800 GB </br></br> 250 Mbps => 900 GB </br></br> 100 Mbps => 360 GB </br></br> 50 Mbps => 180 GB|
|Small to medium enterprise site / Autopilot provisioning center (50 - 500 devices in a single location) |1 - 5 Gbps| 5 Gbps => 18,000 GB </br></br>3 Gbps => 10,800 GB </br></br>1 Gbps => 3,600 GB|
|Medium to large enterprise site / Autopilot provisioning center (500 - 5,000 devices in a single location) |5 - 10 Gbps Peak|   9 Gbps => 32,400 GB </br></br> 5 Gbps => 18,000 GB </br></br>3 Gbps => 10,800 GB|

## Supported content types

Once deployed, Connected Cache can cache content from Microsoft cloud services and deliver it to configured Windows devices on the local network. Connected Cache supports caching of content from most Microsoft cloud services, including:

- Windows updates: Windows feature and quality updates
- Office Click-to-Run apps: Microsoft 365 Apps and updates
- Client apps: Intune, store apps, and updates
- Endpoint protection: Windows Defender definition updates

For the full list of content endpoints that Microsoft Connected Cache for Enterprise and Education supports, see [Microsoft Connected Cache content and services endpoints](delivery-optimization-endpoints.md).

## How it works

The following diagram displays an overview of how Connected Cache functions.

:::image type="content" source="./images/mcc_ent_publicpreview.png" alt-text="Diagram displaying the components of Connected Cache." lightbox="./images/mcc_ent_publicpreview.png":::

1. The Azure management portal for Microsoft Connected Cache is used to create and configure Connected Cache nodes. Azure CLI can also be used to create and configure Connected Cache nodes programmatically.
1. The Connected Cache node is deployed to the host machine using the OS-specific deployment package.

   - For Windows, the Connected Cache deployment package is a Windows application.
   - For Linux, the Connected Cache deployment package is a bundle of bash scripts.

1. The Connected Cache container is deployed to the host machine using Azure IoT Edge container management services. After successful container deployment, the cache node begins reporting status and metrics to Delivery Optimization services.
1. The DOCacheHost policy is applied to managed devices using a Mobile Device Management (MDM) solution such as Intune, a DHCP custom option, or a registry key. This configures the devices to request content from the Connected Cache node instead of directly from a Content Delivery Network (CDN).
1. Devices request content from the cache node > the cache node forwards the requests to the CDN and fills the cache > the cache node delivers the requested content to the devices.
1. Devices can fall back to CDN if the cache node is unavailable. To delay this behavior, set the [DelayCacheServerFallbackForeground/DelayCacheServerFallbackBackground](/windows/deployment/do/waas-delivery-optimization-reference#delay-foreground-download-cache-server-fallback-in-secs) setting to avoid immediate fallback.

The Azure management portal for Connected Cache and Windows Update for Business reports can be used to view usage metrics for Connected Cache nodes and managed devices, respectively.

## Next steps

>[!div class="nextstepaction"]
>[Create Connected Cache Azure resources](mcc-ent-create-resource-and-cache.md)
