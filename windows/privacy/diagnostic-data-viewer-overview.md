---
title: Diagnostic Data Viewer overview
description: Use this article to use the Diagnostic Data Viewer application to review the diagnostic data sent to Microsoft by your device.
ms.service: windows-client
ms.subservice: itpro-privacy
ms.localizationpriority: high
author: DHB-MSFT
ms.author: danbrown
manager: dansimp
ms.date: 07/29/2025
ms.topic: how-to
hideEdit: true
ms.collection: 
- privacy-windows
- must-keep
- trust-pod
---

# Diagnostic Data Viewer overview

**Applies to**

- Windows 11, version 21H2 and later  
- Windows 10, version 1803 and later

The Diagnostic Data Viewer is a Windows app that lets you review the Windows diagnostic data your device is sending to Microsoft, grouping the info into simple categories based on how it's used by Microsoft.

## Install the Diagnostic Data Viewer

You must download the app before you can use the Diagnostic Data Viewer to review your device's diagnostic data. You can download the app from the [Microsoft Store Diagnostic Data Viewer](https://apps.microsoft.com/detail/9n8wtrrsq8f7) page.

> [!NOTE]
> It's possible that your Windows device doesn't have the Microsoft Store available (for example, Windows Server). If this is the case, see [Diagnostic Data Viewer for PowerShell overview](diagnostic-data-viewer-powershell.md).

## Turn on data viewing

Before you can use the app for viewing Windows diagnostic data, you must turn on data viewing in the **Settings** panel. Turning on data viewing lets Windows store your device's diagnostic data until you turn it off. Turning off data viewing stops Windows from collecting your diagnostic data and clears the existing diagnostic data from your device. This setting doesn't affect your data viewing or history for Microsoft 365 Apps or Microsoft Office.

>[!Important]
>Turning on data viewing can use up to 1 GB (by default) of disk space on your system drive. We strongly recommend that you turn off data viewing when you're done using the Diagnostic Data Viewer. For info about turning off data viewing, see the [Turn off data viewing](#turn-off-data-viewing) section later in this article.

To turn on data viewing, do the following steps:

1. Go to **Start**, select **Settings** > **Privacy & security** > **Diagnostics & feedback**.

2. Under **View diagnostic data**, turn on the **Turn on the Diagnostic Data Viewer** option.

## Start the Diagnostic Data Viewer

To start the Diagnostic Data Viewer, do the following steps:

1. Go to **Start**, select **Settings** > **Privacy & security** > **Diagnostics & feedback**.

   (You can also go to **Start** and search for *Diagnostic Data Viewer*.) 

2. Under **View diagnostic data**, select the **Open Diagnostic Data Viewer** button.

3. Close the Diagnostic Data Viewer. Use your device as you normally would for a few days. Then open the Diagnostic Data Viewer again to review the updated list of diagnostic data.

## Use the Diagnostic Data Viewer

The Diagnostic Data Viewer provides you with the following features to view and filter your device's diagnostic data.

### View your Windows diagnostic events

In the left column, you can review your diagnostic events. These events reflect activities that occurred and were sent to Microsoft.

Selecting an event opens the detailed JSON view, which provides the exact details uploaded to Microsoft. Microsoft uses this info to continually improve the Windows operating system.

>[!NOTE]
>Seeing an event doesn't necessarily mean it has been uploaded yet. It’s possible that some events are still queued and will be uploaded at a later time.

![View your diagnostic events.](images/ddv-event-view.jpg)

### Search your diagnostic events

The **Search** box at the top of the screen lets you search among all of the diagnostic event details. The returned search results include any diagnostic event that contains the matching text.

Selecting an event opens the detailed JSON view, with the matching text highlighted.

### Filter your diagnostic event categories

The app's **Menu** button opens the detailed menu. In here, you can find a list of diagnostic event categories, which define how the events are used by Microsoft. Selecting a check box lets you filter between the diagnostic event categories.

### Help to make your Windows experience better

Microsoft only needs diagnostic data from a small number of devices to make big improvements to the Windows operating system and ultimately, your experience. If you’re a part of this small device group and you experience issues, Microsoft collects the associated event diagnostic data, allowing your info to potentially help fix the issue for others.

To signify your contribution, you’ll see this icon (![Icon to review the device-level sampling.](images/ddv-device-sample.png)) if your device is part of the group. In addition, if any of your diagnostic data events are sent from your device to Microsoft to help make improvements, you’ll see this icon (![Icon to review the event-level sampling](images/ddv-event-sample.png)).

### Provide event feedback

The **Feedback** icon in the upper right corner of the window opens the Feedback Hub app, letting you provide feedback about the Diagnostic Data Viewer and the diagnostic events.

Selecting a specific event in the Diagnostic Data Viewer automatically fills in the field in the Feedback Hub. You can add your comments to the box labeled, **Give us more detail (optional)**.

>[!IMPORTANT]
>All content in the Feedback Hub is publicly viewable. Therefore, make sure you don't put any personal info into your feedback comments.

### View a summary of the data you've shared with us over time

The **About your data** in the Diagnostic Data Viewer lets you see an overview of the Windows data you've shared with Microsoft.

Through this feature, you can see how much data you send on average each day, the breakdown of your data by category, the top components and services that have sent data, and more.  

>[!NOTE]
>This content is a reflection of the history of Windows data that the app has stored. If you'd like to have extended analyses, modify the storage capacity of the Diagnostic Data Viewer.

![Screenshot of the "About my data" page in the Diagnostic Data Viewer.](images/ddv-analytics.png) 

## View Microsoft 365 Apps or Microsoft Office diagnostic data

By default, the Diagnostic Data Viewer shows you Windows data. You can also view Microsoft 365 Apps or Microsoft Office diagnostic data by enabling the feature in the app settings page. To learn more about how to view Microsoft 365 Apps or Microsoft Office diagnostic data, see [Using the Diagnostic Data Viewer with Office](https://support.microsoft.com/office/cf761ce9-d805-4c60-a339-4e07f3182855).

## Turn off data viewing

When you're done reviewing your diagnostic data, you should turn off data viewing. This also removes your Windows data history. This setting doesn't affect your data viewing or history for Microsoft 365 Apps or Microsoft Office.

To turn off data viewing, do the following steps:

1. Go to **Start**, select **Settings** > **Privacy & security** > **Diagnostics & feedback**.

2. Under **View diagnostic data**, turn off the **Turn on the Diagnostic Data Viewer** option.

## Modifying the size of your data history

By default, the Diagnostic Data Viewer shows you up to 1 GB or 30 days of data (whichever comes first) for Windows diagnostic data. While the exact volume varies by user, the average device generates approximately 6 MB of Windows diagnostic data per day. Once either the time or space limit is reached, the data is incrementally dropped with the oldest data points dropped first.

> [!Important]
> If you have [diagnostic data viewing enabled](#view-microsoft-365-apps-or-microsoft-office-diagnostic-data) for Microsoft 365 Apps or Microsoft Office, their data history is fixed at 1 GB and cannot be modified.

**Modify the size of your data history**

To make changes to the size of your Windows diagnostic data history, visit the **app settings**, located at the bottom of the navigation menu. Data is incrementally dropped with the oldest data points first once your chosen size or time limit is reached.  

> [!Important]
> Decreasing the maximum amount of diagnostic data viewable through the tool will remove all data history and requires a reboot of your device. Additionally, increasing the maximum amount of diagnostic data viewable by the tool may come with performance impacts to your machine.

## View additional diagnostic data in the "View problem reports" tool

Available on Windows 10 (version 1809 and higher) and on Windows 11, you can review additional Windows Error Reporting diagnostic data in the **View problem reports** page within the Diagnostic Data Viewer.

This page provides you with a summary of various crash reports that are sent to Microsoft as part of Windows Error Reporting. We use this data to find and fix specific issues that are hard to replicate and to improve the Windows operating system.

You can also use the Windows Error Reporting tool available in the Control Panel.

### To view your Windows Error Reporting diagnostic data using the Diagnostic Data Viewer

On Windows 10 (version 1809 and higher) and on Windows 11, you can review Windows Error Reporting diagnostic data in the Diagnostic Data Viewer.  

![Screenshot of the "Problem reports" section of the Diagnostic Data Viewer.](images/ddv-problem-reports.png)

### To view your Windows Error Reporting diagnostic data using the Control Panel

To use the Windows Error Reporting tool in the Control Panel, you can do either of the following steps:

- Go to **Start**, select **Control Panel** > **All Control Panel Items** > **Security and Maintenance** > **Problem Reports**.
- Go to **Start** and search for *Problem Reports*.

The **Review problem reports** tool opens, showing you your Windows Error Reporting reports, along with a status about whether it was sent to Microsoft.

![Screenshot of the "Review problem reports" tool in Control Panel.](images/control-panel-problem-reports-screen.png)

> [!IMPORTANT]
> To inquire about Windows data access or interoperability related to the Digital Markets Act (DMA), [submit this form](https://go.microsoft.com/fwlink/p/?linkid=2271128).
