---
title: Testing Methodology
description: Testing Methodology Information
ms.date: 06/27/2025
ms.service: windows-client
ms.subservice: itpro-fundamentals
ms.localizationpriority: medium
author: mestew
ms.author: mstewart
manager: bpardi
ms.topic: reference
ms.collection:
  - tier3
appliesto:
  - ✅ <a href="https://learn.microsoft.com/windows/release-health/supported-versions-windows-client" target="_blank">Windows 11</a>
--- 

# Testing Methodology

This section consolidates the documented steps for running a selection of synthetic benchmarks Microsoft uses in performance evaluation. Below is a nonexhaustive list of benchmarks regularly used by Microsoft for device testing, with the respective testing process.

> [!Note] 
> Some tools used in performance evaluations require the use of third-party benchmarks that are subject to licensing or usage fees, and others may require licensing or usage fees to enable offline testing and prevent automatic uploading of results to online databases. 
>
> If application or benchmark updates introduce changes that impact the steps documented here or if version information changes, users should refer directly to the official documentation or in-app instructions for the most up-to-date and accurate execution procedures instead of relying solely on the steps listed below.

## Device setup 

- Complete the Out of Box experience, selecting default settings.

- Check that the date and time are correct.

- In **Settings**, go to **System** > **Power & battery**. Under **Screen, sleep, & hibernate timeouts**, select **Never** for **Turn my screen off after** and **Make my device sleep after**. 

- In **Settings**, go to **Windows Update** and check for updates to install them.

- In Microsoft Store, go to **Downloads** > **Check for updates** and install them.

- Open Microsoft Edge browser and complete Edge setup including any available updates.

- Install all Benchmarks and tests using default settings.

- For Procyon® Office - Microsoft 365 or Office applications are required, these may need to be purchased.

- Run a full antivirus scan. 

- Pause Windows Updates before running any tests.

- Don't re-enable networking while the benchmark is running.

- Don't launch the benchmark while networking is enabled. 

- Gather results, exit benchmark.

- Prior to testing ensure that the device is fully charged.

- Reboot the device and leave it idle for at least 15 minutes prior to running any tests.

## Required Steps Prior to Launching Benchmarking Procedures

Prior to launching any benchmark, follow the procedures below:

1. Disable Wi-Fi.

   1. Go to Device Manager and disable Wi-Fi device.

1. Disable Ethernet if supported. 

1. Physically disconnect ethernet connection if supported.

1. Turn on airplane mode.

1. Before launching any benchmark, reconfirm that networking is disabled.

1. Reboot the device.

1. Wait 15 minutes before running any tests. 

> [!Note]
> This procedure is required for all benchmarks except those that have an inherent requirement for a network connection. For this (and all) benchmarks, we expect you to use your best efforts to do the following: (i) purchase a fully licensed version of the test (to prevent automatic upload and/or sharing of test results); or (ii) select the appropriate options to disable automatic uploading and/or sharing of test results.

## Cinebench® R24

Download and install Cinebench® R24 from Maxon ([link](https://www.maxon.net/en/downloads/cinebench-2024-downloads)).

### Running the test 

1. Launch Cinebench®.

1. Select **Start** next to the test you want to run on the top left of the screen.

1. When the test is completed, record the results.

1. Wait 15 minutes before rerunning.

## Procyon® Office

Download and install Procyon® Office Productivity benchmark from UL ([link](https://benchmarks.ul.com/procyon/office-productivity-benchmark)).

This test runs both the Procyon® Office Productivity benchmark and Procyon® Office Productivity benchmark MP (multi-platform). Windows Performance Lab recommends running both and the procedure described below can be applied to both.

### Setting up the test

1. Install a licensed version of Microsoft 365 and launch the following applications at least twice verifying that the applications are signed in and updated: Microsoft Excel, Microsoft PowerPoint, Microsoft Word, and Microsoft Outlook.

1. Launch Procyon®.

1. Select **Settings** and input the Procyon® Office Productivity license key.

1. Close Procyon®.

### Running the test 

1. Launch Procyon® and verify licensed version is in use.

1. Select **Test Suite**.

1. Select **Office Productivity** test.

1. Select **Run** to begin the test.

1. When the test is completed, record the results.

1. Wait 15 minutes before rerunning.

## Procyon® AI Computer Vision

Download and install Procyon® AI Computer Vision Benchmark from UL ([link](https://benchmarks.ul.com/procyon))

### Setting up the test

1. Launch Procyon®.

1. Enter the registration code.

1. Check for and install any updates.

1. Close Procyon®.

### Running the test

1. Launch Procyon®. 

1. On the **My suite** page, **Select AI Computer Vision Benchmark**.

1. Select the corresponding test for your silicon and select **Run**.

1. When the test is completed, record the results.

1. Wait 15 minutes before rerunning.

## 3DMark® 

Download and install 3DMark® benchmark from UL ([link](https://benchmarks.ul.com/3dmark)).

### Setting up the test

1. Launch 3DMark®.

1. Enter the registration code.

1. Check for and install any updates.

1. Close 3DMark®.

### Running the test

1. Launch 3DMark®.

1. On the 3DMark® main page, select **Run** underneath the benchmark of your choice.

1. When the test is completed, record the results.

1. Wait 15 minutes before rerunning.

## Geekbench®

Download and install Geekbench® 6 using default settings ([link](https://www.geekbench.com/)).

### Running the test

1. Launch Geekbench®.

1. Click **Run** on the benchmark of your choice.

1. Record the result.

## In-game Benchmarks

### Setting up the tests

1. Launch the game.

1. Locate the benchmark settings within the title.

### Running the test

1. The benchmarks are typically located in Graphics sections of the settings within the game (for example, Shadow of the Tomb Raider®: Display and Graphics; Cyberpunk 2077®: Graphics, B).

1. Run benchmark.

1. When the test is completed, record the results.

1. Wait 15 minutes before rerunning.

## Windows Assessment and Deployment Kit (ADK) Web Browsing / Local Video Playback / Streaming

*(Coming soon)*

[!INCLUDE [Detailed Test Results](./includes/detailed-test-results.md)]


