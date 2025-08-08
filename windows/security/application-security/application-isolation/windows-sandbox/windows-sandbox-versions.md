---
title: Windows Sandbox versions
description: Windows Sandbox versions
ms.topic: article
ms.date: 10/22/2024
---

# Windows Sandbox versions

Starting with Windows 11, version 24H2, a newer version of Windows Sandbox is available from the Microsoft Store, featuring an improved user experience and new command line functionality.

- **Faster Updates**: With the app now being updated through the Microsoft Store, you can install the bug fixes and new features as soon as they're available, rather than needing to wait for an update of the Windows operating system.
- **Revamped UI**: The app now features WinUI 3, a modern and sleek user interface built on the Fluent design system.
- **New Runtime Features**: Users can now access clipboard redirection, audio/video input control, and folder sharing directly during runtime using the "…" icon in the top-right corner without needing a preconfigured `.wsb` file.
- **Command Line Preview**: An early version of [command line support](windows-sandbox-cli.md) for Windows Sandbox is now available.

## Upgrading to the newer version

### Prerequisites

- Windows Sandbox must already be installed. If it isn't already installed, [install Windows Sandbox](windows-sandbox-install.md).
- Device must be running Windows 11, version 24H2, with KB10D or later.
- Internet access for Microsoft Store and Windows Update.

### Upgrade

- Launch **Windows Sandbox** from the Start menu.
- If the app isn't upgraded to the latest version, a progress dialog appears as it automatically attempts to update. This process typically takes 30 seconds to 2 minutes.
- Once the installation is complete, you're directed to the updated version of the app.

> [!NOTE]
> If the upgrade fails on the first try, the installation continues in the background while you use the older version of the app. Additionally, the app is queued in the "Updates & downloads" section of the Microsoft Store app for users who wish to install it manually.