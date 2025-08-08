---
title: Use and configure Windows Sandbox
description: Use and configure Windows Sandbox
ms.topic: how-to
ms.date: 09/09/2024
---

# Use and configure Windows Sandbox

To launch a Windows Sandbox with default settings, locate and select Windows Sandbox on the Start menu or search for 'Windows Sandbox'. This launches a basic Sandbox with maximum capacity of 4GB memory with the following properties:

- **vGPU (virtualized GPU)**: Enabled on non-Arm64 devices.
- **Networking**: Enabled. The sandbox uses the Hyper-V default switch.
- **Audio input**: Enabled. The sandbox shares the host's microphone input into the sandbox.
- **Video input**: Disabled. The sandbox doesn't share the host's video input into the sandbox.
- **Protected client**: Disabled. The sandbox doesn't use increased security settings on the Remote Desktop Protocol (RDP) session.
- **Printer redirection**: Disabled. The sandbox doesn't share printers with the host.
- **Clipboard redirection**: Enabled. The sandbox shares the host clipboard with the sandbox so that text and files can be pasted back and forth.

> [!IMPORTANT]
>
> - Networking is enabled by default. This can expose untrusted applications to the internal network. To launch a Sandbox with networking disabled, use a custom .wsb file.
> - With Clipboard redirection automatically enabled, you can easily copy files from the host and paste them into the Windows Sandbox window.

You have the freedom to open files, install applications from the web, and perform various other tasks that benefit from an isolated clean environment.

When you're finished experimenting, close the sandbox. A dialog box prompts you to confirm the deletion of all sandbox content. Select **Ok** to proceed. Confirm that your host machine doesn't exhibit any of the modifications that you made in Windows Sandbox.

## Configure a custom Windows Sandbox

Windows Sandbox supports simple configuration files, which provide a minimal set of customization parameters for Sandbox. This feature can be used with Windows 10 build 18342 or Windows 11. Windows Sandbox configuration files are formatted as XML and are associated with Sandbox via the `.wsb` file extension.

A configuration file enables the user to control the following aspects of Windows Sandbox:

- **vGPU (virtualized GPU)**: Enable or disable the virtualized GPU. If vGPU is disabled, the sandbox uses Windows Advanced Rasterization Platform (WARP).
- **Networking**: Enable or disable network access within the sandbox.
- **Mapped folders**: Share folders from the host with *read* or *write* permissions. Exposing host directories might allow malicious software to affect the system or steal data.
- **Logon command**: A command to execute when Windows Sandbox starts.
- **Audio input**: Shares the host's microphone input into the sandbox.
- **Video input**: Shares the host's webcam input into the sandbox.
- **Protected client**: Places increased security settings on the Remote Desktop Protocol (RDP) session to the sandbox.
- **Printer redirection**: Shares printers from the host into the sandbox.
- **Clipboard redirection**: Shares the host clipboard with the sandbox so that text and files can be pasted back and forth.
- **Memory in MB**: The amount of memory, in megabytes, to assign to the sandbox.

> [!NOTE]
> The size of the sandbox window currently isn't configurable. <!-- windows-itpro-docs #10689 -->

## Create a configuration file

To create a configuration file:

1. Open a plain text editor or source code editor (for example, Notepad, Visual Studio Code, etc.)
2. Insert the following lines:

    ```XML
    <Configuration>
    </Configuration>
    ```

3. Add appropriate configuration text between the two lines. For details, see [examples](windows-sandbox-sample-configuration.md).
4. Save the file with the desired name, but make sure its filename extension is `.wsb`. In Notepad, you should enclose the filename and the extension inside double quotation marks, for example, `"MyConfigFile.wsb"`.

To use a configuration file, double-click it to start Windows Sandbox according to its settings. You can also invoke it via the command line as shown here:

```batch
C:\Temp> MyConfigFile.wsb
```

## Configuration options

### vGPU

Enables or disables GPU sharing.

```xml
<vGPU>value</vGPU>
```

Supported values:

- **Enable**: Enables vGPU support in the sandbox.
- **Disable**: Disables vGPU support in the sandbox. If this value is set, the sandbox uses software rendering, which might be slower than virtualized GPU.
- **Default**: This value is the default value for vGPU support. Currently, this default value denotes that vGPU is enabled.

> [!NOTE]
> Enabling virtualized GPU can potentially increase the attack surface of the sandbox.

### Networking

Enables or disables networking in the sandbox. You can disable network access to decrease the attack surface exposed by the sandbox.

```xml
<Networking>value</Networking>
```

Supported values:

- **Enable**: Enables networking in the sandbox.
- **Disable**: Disables networking in the sandbox.
- **Default**: This value is the default value for networking support. This value enables networking by creating a virtual switch on the host and connects the sandbox to it via a virtual NIC.

> [!NOTE]
> Enabling networking can expose untrusted applications to the internal network.

### Mapped folders

An array of folders, each representing a location on the host machine that is shared with the sandbox at the specified path. Currently, relative paths aren't supported.

When using `<Mappedfolders>` to map folders, the folders are mapped before the execution of the [Logon command](#logon-command). Beginning in Windows 11, version 23H2, you can use environment variables in the path.

```xml
<MappedFolders>
  <MappedFolder>
    <HostFolder>absolute or relative path to the host folder</HostFolder>
    <SandboxFolder>absolute path to the sandbox folder</SandboxFolder>
    <ReadOnly>value</ReadOnly>
  </MappedFolder>
  <MappedFolder>
    ...
  </MappedFolder>
</MappedFolders>
```

- **HostFolder**: Specifies the folder on the host machine to share into the sandbox. The folder must already exist on the host, or the container fails to start.
- **SandboxFolder**: Specifies the destination in the sandbox to map the folder to. If the folder doesn't exist, it gets created. If no sandbox folder is specified, the folder is mapped to the container user's desktop. The default user of Sandbox is `WDAGUtilityAccount`.
- **ReadOnly**: If *true*, enforces read-only access to the shared folder from within the container. Supported values: *true*/*false*. Defaults to *false*.

> [!NOTE]
> Files and folders mapped from the host can be compromised by apps in the sandbox or potentially affect the host. Changes made during a Sandbox session to a mapped folder with write-permissions will persist after a Sandbox is disposed.

### Logon command

Specifies a single command that will be invoked automatically after the sandbox logs on. Apps in the sandbox are run under the container user account. The container user account should be an administrator account.

```xml
<LogonCommand>
  <Command>command to be invoked</Command>
</LogonCommand>
```

**Command**: A path to an executable or script inside the container that will be executed after signing in.

> [!NOTE]
> Although very simple commands will work (such as launching an executable or script), more complicated scenarios involving multiple steps should be placed into a script file. This script file may be mapped into the container via a shared folder, and then executed via `<LogonCommand>`.

### Audio input

Enables or disables audio input to the sandbox.

```xml
<AudioInput>value</AudioInput>
```

Supported values:

- **Enable**: Enables audio input in the sandbox. If this value is set, the sandbox can receive audio input from the user. Applications that use a microphone might require this capability.
- **Disable**: Disables audio input in the sandbox. If this value is set, the sandbox can't receive audio input from the user. Applications that use a microphone might not function properly with this setting.
- **Default**: This value is the default value for audio input support. Currently, this default value denotes that audio input is enabled.

> [!NOTE]
> There may be security implications of exposing host audio input to the container.

### Video input

Enables or disables video input to the sandbox.

```xml
<VideoInput>value</VideoInput>
```

Supported values:

- **Enable**: Enables video input in the sandbox.
- **Disable**: Disables video input in the sandbox. Applications that use video input might not function properly in the sandbox.
- **Default**: This value is the default value for video input support. Currently, this default value denotes that video input is disabled. Applications that use video input might not function properly in the sandbox.

> [!NOTE]
> There may be security implications of exposing host video input to the container.

### Protected client

When Protected Client mode is enabled, Sandbox adds a new layer of security boundary by running inside an [AppContainer Isolation](/windows/win32/secauthz/appcontainer-isolation) execution environment. AppContainer Isolation provides Credential, Device, File, Network, Process, and Window isolation.

```xml
<ProtectedClient>value</ProtectedClient>
```

Supported values:

- **Enable**: Runs Windows sandbox in Protected Client mode. If this value is set, the Sandbox runs in AppContainer Isolation.
- **Disable**: Runs the Sandbox in the standard mode without extra security mitigations.
- **Default**: This value is the default value for Protected Client mode. Currently, this default value denotes that the sandbox doesn't run in Protected Client mode.

> [!NOTE]
> This setting may restrict the user's ability to copy/paste files in and out of the sandbox.

### Printer redirection

Enables or disables printer sharing from the host into the sandbox.

```xml
<PrinterRedirection>value</PrinterRedirection>
```

Supported values:

- **Enable**: Enables sharing of host printers into the sandbox.
- **Disable**: Disables printer redirection in the sandbox. If this value is set, the sandbox can't view printers from the host.
- **Default**: This value is the default value for printer redirection support. Currently, this default value denotes that printer redirection is disabled.

### Clipboard redirection

Enables or disables sharing of the host clipboard with the sandbox.

```xml
<ClipboardRedirection>value</ClipboardRedirection>
```

Supported values:

- **Enable**: Enables sharing of the host clipboard with the sandbox.
- **Disable**: Disables clipboard redirection in the sandbox. If this value is set, copy/paste in and out of the sandbox is restricted.
- **Default**: This value is the default value for clipboard redirection. Currently, copy/paste between the host and sandbox are permitted under *Default*.

### Memory in MB

Specifies the amount of memory that the sandbox can use in megabytes (MB).

```xml
<MemoryInMB>value</MemoryInMB>
```

If the memory value specified is insufficient to boot a sandbox, it's automatically increased to the required minimum amount of 2048 MB.
