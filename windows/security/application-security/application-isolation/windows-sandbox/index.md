---
title: Windows Sandbox
description: Windows Sandbox overview
ms.topic: overview
ms.date: 09/09/2024
---

# Windows Sandbox

Windows Sandbox (WSB) offers a lightweight, isolated desktop environment for safely running applications. It's ideal for testing, debugging, exploring unknown files, and experimenting with tools. Applications installed within the sandbox remain isolated from the host machine using hypervisor-based virtualization. As a disposable virtual machine (VM), Windows Sandbox ensures reboot persistence, quick launch times, and a lower memory footprint compared to full VMs. Its one-click setup simplifies the user experience.

The sandbox is temporary; closing it deletes all software, files, and state. Each launch provides a fresh instance. Host-installed software isn't available in the sandbox. Applications needed within the sandbox must be installed there explicitly.

> [!NOTE]
> Starting with Windows 11, version 22H2, data persists through restarts initiated within the sandbox, useful for applications requiring a reboot.

Windows Sandbox offers the following features:

- **Part of Windows**: Everything required for this feature is included in the supported Windows editions like Pro, Enterprise, and Education. There's no need to maintain a separate VM installation.
- **Disposable**: Nothing persists on the device. Everything is discarded when the user closes the application.
- **Pristine**: Every time Windows Sandbox runs, it's as clean as a brand-new installation of Windows.
- **Secure**: Uses hardware-based virtualization for kernel isolation. It relies on the Microsoft hypervisor to run a separate kernel that isolates Windows Sandbox from the host.
- **Efficient**: Takes a few seconds to launch, supports virtual GPU, and has smart memory management that optimizes memory footprint.

> [!IMPORTANT]
> Windows Sandbox enables network connection by default. It can be disabled using the [Windows Sandbox configuration file](windows-sandbox-configure-using-wsb-file.md#networking). Enabling networking can expose untrusted applications to the internal network.

WSB can be used without any technical skills in various scenarios where users need a secure, clean environment for testing or running potentially harmful software. Here are some ways in which you can use WSB:

- **Clean environment for software testing**: Test or debug your applications in WSB's clean environment to identify and resolve bugs or compatibility issues.
- **Secure web browsing**: Use WSB for secure web browsing, especially when accessing unfamiliar or potentially dangerous websites without putting your system at risk of malware infection.
- **Running Untrusted Applications**: Mitigate security risks by opening untrusted applications or files, such as email attachments in WSB. Improve your safety and security by opening a sandbox with networking disabled and mapping the folder with the application or file you want to open to the sandbox in read-only mode. Check [Sample configuration files](windows-sandbox-sample-configuration.md) for more details.
- **Testing or demoing new software for the first time**: Test drive or demo new software, preview versions, extensions, or add-ons without the hassle of installing and then uninstalling on your host machine.
- **Maintaining multiple dev environments**: Streamline your development process by utilizing WSB to maintain multiple sandboxes for different development environments. For example, maintain a sandbox for each python version and its dependencies!

> [!NOTE]
> Windows Sandbox currently doesn't allow multiple instances to run simultaneously.


[!INCLUDE [windows-sandbox](../../../../../includes/licensing/windows-sandbox.md)]

> [!NOTE]
> Windows Sandbox is currently not supported on Windows Home edition.
