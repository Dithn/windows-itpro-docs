---
title: Shell Launcher Overview
description: Learn how to configure devices with Shell Launcher.
ms.date: 3/7/2025
ms.topic: overview
---

# Shell Launcher overview

Shell Launcher is a Windows feature that you can use to replace the default Windows Explorer shell (`Explorer.exe`) with a Windows desktop application or a Universal Windows Platform (UWP) app. This feature is useful for creating a custom user experience on devices that are used for a specific purpose, including kiosks, ATMs, and digital signage.

Shell Launcher controls which application a user gets as the shell after sign-in. It doesn't prevent a user from accessing other desktop applications and system components. From a custom shell, you can launch secondary views displayed on multiple monitors, or launch other apps in full screen on user's demand. You can also configure Shell Launcher to launch different shell applications for different users or user groups.

With Shell Launcher, you can use features and methods to control access to other applications or system components. These methods include, but aren't limited to:

- Configuration Service Provider (CSP)
- Group policy (GPO)
- [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview)

[!INCLUDE [shell-launcher](../../../includes/licensing/shell-launcher.md)]

## Shell Launcher version history

Shell Launcher has undergone several iterations since its introduction, with the most notable being Shell Launcher v1 and Shell Launcher v2. Each version has brought improvements and new features to enhance the user experience and functionality of custom shells in Windows environments:

- Shell Launcher v1 was the original implementation, introduced to provide basic functionality for replacing the default shell. However, it had limitations, such as only supporting Win32 applications as custom shells and lacking flexibility for handling modern app scenarios
- Shell Launcher v2, introduced with Windows 10, version 1809, added support for Universal Windows Platform (UWP) apps as custom shells, making it more versatile for modern environments

### Differences between Shell Launcher v1 and Shell Launcher v2

- Shell Launcher v1 replaces `Explorer.exe` with `Eshell.exe`, which can only launch a Windows desktop application
- Shell Launcher v2 replaces `Explorer.exe` with `CustomShellHost.exe`, which can launch a Windows desktop application or a UWP app
- In addition to allowing you to use a UWP app for your replacement shell, Shell Launcher v2 offers more enhancements:
  - You can use a custom Windows desktop application that can then launch UWP apps, such as Settings and Touch Keyboard
  - From a custom UWP shell, you can launch secondary views and run on multiple monitors
  - The custom shell app runs in full screen, and can run other apps in full screen on user's demand

For sample XML configurations for the different app combinations, see [Samples for Shell Launcher v2](https://github.com/microsoft/Windows-IoT-Samples/tree/master/samples/ShellLauncher/ShellLauncherV2).

## Limitations

Here are some limitations to consider when using Shell Launcher:

- Windows doesn't support setting a custom shell before the out-of-box experience (OOBE). If you do, you can't deploy the resulting image
- Shell Launcher doesn't support a custom shell with an application that launches a different process and exits. For example, you can't specify `write.exe` in Shell Launcher. Shell Launcher launches a custom shell and monitors the process to identify when the custom shell exits. `Write.exe` creates a 32-bit `wordpad.exe` process and exits. Since Shell Launcher isn't aware of the newly created `wordpad.exe` process, Shell Launcher takes action based on the exit code of `Write.exe`, such as restarting the custom shell

## Shell Launcher user rights

A custom shell is launched with the same level of user rights as the account that is signed in. This means that a user with administrative rights can perform any system action that requires administrative rights, including launching other applications with administrative rights.

> [!WARNING]
> If your shell application requires administrative rights and needs to be elevated, and User Account Control (UAC) is enabled, you must disable UAC for Shell Launcher to launch the shell application.

## Next steps

> [!div class="nextstepaction"]
> Learn how to configure Shell Launcher:
>
> [Configure Shell Launcher](configure.md)

### :::image type="icon" source="../images/icons/rocket.svg" border="false"::: Quickstarts

If you want to quickly test Shell Launcher, check out the following quickstart:

- [Quickstart: configure a kiosk with Shell Launcher](quickstart-kiosk.md)
