---
title: Verify Microsoft Connected Cache for Enterprise and Education cache node functionality
description: Details on how to verify functionality of Microsoft Connected Cache for Enterprise and Education cache nodes.
author: chrisjlin
ms.author: lichris
manager: naengler
ms.service: windows-client
ms.subservice: itpro-updates
ms.topic: how-to
ms.date: 07/23/2025
appliesto: 
- ✅ Windows-hosted Connected Cache cache nodes
- ✅ Linux-hosted Connected Cache cache nodes
- ✅ <a href=https://learn.microsoft.com/windows/deployment/do/waas-microsoft-connected-cache target=_blank>Microsoft Connected Cache for Enterprise and Education</a>	
---

# Verify Connected Cache node functionality

This article describes how to verify that a Microsoft Connected Cache for Enterprise and Education cache node is functioning correctly.

These steps should be taken after deploying Connected Cache software to a [Windows](mcc-ent-deploy-to-windows.md) or [Linux](mcc-ent-deploy-to-linux.md) host machine.

If you're deploying Connected Cache to an environment with a network proxy, follow step 1 and 2 and verify that these calls don't get blocked by your network proxy.

## Steps to verify functionality of Connected Cache node

1. To verify that the Connected Cache container on the host machine is running and reachable, run the following command from the host machine:

    ```powershell
    wget http://localhost/filestreamingservice/files/7bc846e0-af9c-49be-a03d-bb04428c9bb5/Microsoft.png?cacheHostOrigin=dl.delivery.mp.microsoft.com
    ```

    If successful, there should be an HTTP response with StatusCode 200.

1. To verify that Windows client devices in your network can reach the Connected Cache node, visit the following address from a web browser on a Windows client device:

    `http://[HostMachine-IP-address]/filestreamingservice/files/7bc846e0-af9c-49be-a03d-bb04428c9bb5/Microsoft.png?cacheHostOrigin=dl.delivery.mp.microsoft.com`

    If successful, the Windows client device should begin to download a small image file from the Connected Cache node.

## Configure Windows clients to use Connected Cache node

1. To configure a Windows client device to request content from a Connected Cache node, you need to set the device's [DOCacheHost](waas-delivery-optimization-reference.md#cache-server-hostname) or [DOCacheHostSource](waas-delivery-optimization-reference.md#cache-server-hostname) policies. This can be done using your preferred Mobile Device Management (MDM) software or Group Policy. More information on configuring these policies can be found in the [Delivery Optimization configuration documentation](delivery-optimization-configure.md#3-using-connected-cache).

1. To check how much content an individual Windows client has downloaded from a Connected Cache node, open the [Delivery Optimization activity monitor](/microsoft-365-apps/updates/delivery-optimization#viewing-data-about-the-use-of-delivery-optimization) on the Windows client device.

    You should see a donut chart titled **Download Statistics**. If the Windows client has downloaded content from the cache node, you'll see a segment of the donut labeled **From Microsoft cache server**. This segment currently aggregates all content downloaded from any Connected Cache node, so it may not be possible to determine which specific cache node the content was downloaded from.

## Related content

- [Monitor cache node usage](mcc-ent-monitoring.md)
- [Troubleshoot cache node](mcc-ent-troubleshooting.md)
