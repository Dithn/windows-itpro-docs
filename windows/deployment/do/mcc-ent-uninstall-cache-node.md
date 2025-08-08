---
title: Uninstall Microsoft Connected Cache for Enterprise and Education cache nodes
description: Details on how to uninstall Microsoft Connected Cache for Enterprise and Education from a host machine.
ms.service: windows-client
ms.subservice: itpro-updates
ms.topic: how-to
ms.author: lichris
author: chrisjlin
manager: naengler
appliesto: 
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 11</a>
- ✅ Supported Linux distributions
- ✅ <a href=https://learn.microsoft.com/windows/deployment/do/waas-microsoft-connected-cache target=_blank>Microsoft Connected Cache for Enterprise and Education</a> 
ms.date: 07/23/2025
---

# Uninstall Connected Cache software from a host machine

This article describes how to uninstall Microsoft Connected Cache for Enterprise and Education caching software from a host machine. These steps should be taken after deleting the cache node in the Azure portal.

## Steps to uninstall Connected Cache from a Windows host machine

1. Launch a PowerShell window *as administrator* and navigate to the directory returned by `$(deliveryoptimization-cli mcc-get-scripts-path)`.
1. Run the `uninstallmcconwsl.ps1` script, passing in the runtime account credentials you designated during cache node deployment.

    **For Local User Accounts:**

   ```powershell
   .\uninstallmcconwsl.ps1 -mccLocalAccountCredential $myLocalAccountCredential
   ```

    **For Group Managed Service Accounts:**

   ```powershell
   .\uninstallmcconwsl.ps1 -RunTimeAccountName "DOMAIN\ServiceAccountName$"
   ```

This script will remove the Connected Cache container, IoT Edge, and all related components from the host machine. To avoid impact to non Connected Cache workloads, don't deploy Connected Cache to host machines with any Azure IoT Edge modules already installed.

This will also unregister the Connected Cache application from the host machine, stopping it from receiving further updates.

### Uninstall the Connected Cache application

To completely uninstall the Connected Cache application, run the following command in an elevated PowerShell window.

```powershell
Get-AppxPackage -AllUsers Microsoft.DeliveryOptimization | Remove-AppxPackage -AllUsers
```

This command removes the Connected Cache application and Connected Cache install scripts for all users on the host machine.

## Steps to uninstall Connected Cache from a Linux host machine

The `uninstallmcc.sh` script within the deployment package uninstalls the Connected Cache caching software and all related components, including:

- IoT Edge
- IoT Edge Agent
- IoT Edge Hub
- Connected Cache container
- Moby CLI
- Moby engine

To avoid impact to non Connected Cache workloads, don't deploy Connected Cache to host machines with any Azure IoT Edge modules already installed.
