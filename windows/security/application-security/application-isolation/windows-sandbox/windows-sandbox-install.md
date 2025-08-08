---
title: Install Windows Sandbox
description: Install Windows Sandbox
ms.topic: how-to
ms.date: 09/09/2024
---

# Install Windows Sandbox

## Prerequisites

- Arm64 (for Windows 11, version 22H2 and later) or AMD64 architecture
- Virtualization capabilities enabled in BIOS
- At least 4 GB of RAM (8 GB recommended)
- At least 1 GB of free disk space (SSD recommended)
- At least two CPU cores (four cores with hyper-threading recommended)

> [!NOTE]
> Beginning in Windows 11, version 24H2, inbox store apps like Calculator, Photos, Notepad and Terminal are not available inside Windows Sandbox. Ability to use these apps will be added soon.

## Installation

1. Ensure that your machine is using Windows 11 or Windows 10, version 1903 or later.

2. Enable virtualization on the machine.

   - If you're using a physical machine, make sure virtualization capabilities are enabled in the BIOS.
   - If you're using a virtual machine, you need to enable nested virtualization. If needed, also update the VM to support nested virtualization. Run the following PowerShell commands on the host:

     ```powershell
     Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true
     Update-VMVersion -VMName <VMName>
     ```

3. Use the search bar on the task bar and type **Turn Windows Features on or off** to access the Windows Optional Features tool. Select **Windows Sandbox** and then **OK**. Restart the computer if you're prompted.

   If the **Windows Sandbox** option is unavailable, your computer doesn't meet the requirements to run Windows Sandbox. If you think this analysis is incorrect, review the prerequisite list and steps 1 and 2.

   > [!NOTE]
   > To enable Sandbox using PowerShell, open PowerShell as Administrator and run the following command:
   >
   > ```powershell
   > Enable-WindowsOptionalFeature -FeatureName "Containers-DisposableClientVM" -All -Online
   > ```

4. Locate and select **Windows Sandbox** on the Start menu to run it for the first time.

   > [!NOTE]
   > Beginning in Windows 11, version 24H2, Windows Sandbox adheres to the mouse settings of the host system.
   >
   > If you are on an older build and if the host system is set to use a left-handed mouse, you must apply these settings in Windows Sandbox manually when Windows Sandbox starts. Alternatively, you can use a sandbox configuration file to run a logon command to swap the mouse setting. For an example, see [Example 3](windows-sandbox-sample-configuration.md#example-3---mapping-folders-and-running-a-powershell-script-as-a-logon-command).

## Try WSB preview features by joining the Windows Insider Program

To try the most recent features or updates to WSB, join the [Windows Insiders Program](https://insider.windows.com/getting-started). After joining the Windows Insiders Program, you can choose the channel you would like to receive preview builds from inside the Windows settings menu. You can choose from:

- **Dev channel**: Most recent updates, but low stability.
- **Beta channel**: Ideal for early adopters, more reliable builds than the Dev channel.
- **Release Preview channel**: Preview fixes and key features on the next version of Windows just before its available to the general public.
