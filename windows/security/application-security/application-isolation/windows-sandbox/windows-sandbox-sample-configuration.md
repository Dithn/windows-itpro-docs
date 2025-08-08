---
title: Windows Sandbox sample configuration files
description: Windows Sandbox sample configuration files
ms.topic: how-to
ms.date: 09/09/2024
---

# Windows Sandbox sample configuration files

## Example 1 - Mapping Folders and testing an unknown downloaded file in a Sandbox

The following config file can be used to easily test unknown downloaded files inside a sandbox. To achieve this testing, networking and vGPU are disabled, and the sandbox is allowed read-only access to the downloads folder from the host and is placed inside a 'temp' folder in the sandbox. For convenience, the logon command opens the downloads folder inside the sandbox when it's started.

### Downloads.wsb

```xml
<Configuration>
  <VGpu>Disable</VGpu>
  <Networking>Disable</Networking>
  <MappedFolders>
    <MappedFolder>
      <HostFolder>C:\Users\Public\Downloads</HostFolder>
      <SandboxFolder>C:\temp</SandboxFolder>
      <ReadOnly>true</ReadOnly>
    </MappedFolder>
  </MappedFolders>
  <LogonCommand>
    <Command>explorer.exe C:\temp</Command>
  </LogonCommand>
</Configuration>

```

## Example 2 - Installing Visual Studio Code at launch in a Sandbox

The following config file installs Visual Studio Code in the sandbox, which requires a slightly more complicated LogonCommand setup.

Two folders are mapped into the sandbox; the first (`SandboxScripts`) contains VSCodeInstall.cmd, which installs and runs Visual Studio Code. The second folder (`CodingProjects`) is assumed to contain project files that the developer wants to modify using Visual Studio Code.

With the Visual Studio Code installer script already mapped into the sandbox, the `<LogonCommand>` can reference it.

### VSCodeInstall.cmd

This batch file should be created in the `C:\SandboxScripts` directory on the host. It downloads VS Code to `temp` folder inside the sandbox and runs installation from `temp` folder.

```batch
REM Download Visual Studio Code
curl -L "https://update.code.visualstudio.com/latest/win32-x64-user/stable" --output C:\temp\vscode.exe

REM Install and run Visual Studio Code
C:\temp\vscode.exe /verysilent /suppressmsgboxes
```

### VSCode.wsb

```xml
<Configuration>
  <MappedFolders>
    <MappedFolder>
      <HostFolder>C:\SandboxScripts</HostFolder>
      <SandboxFolder>C:\temp\sandbox</SandboxFolder>
      <ReadOnly>true</ReadOnly>
    </MappedFolder>
    <MappedFolder>
      <HostFolder>C:\CodingProjects</HostFolder>
      <SandboxFolder>C:\temp\Projects</SandboxFolder>
      <ReadOnly>false</ReadOnly>
    </MappedFolder>
  </MappedFolders>
  <LogonCommand>
    <Command>C:\temp\sandbox\VSCodeInstall.cmd</Command>
  </LogonCommand>
</Configuration>
```

## Example 3 - Mapping Folders and running a PowerShell script as a Logon Command

Beginning in Windows 11, version 24H2, Windows Sandbox adheres to the mouse settings of the host system. If you are on an older build and if the host system is set to use a left-handed mouse, you must apply these settings in Windows Sandbox manually when Windows Sandbox starts. Alternatively, you can use a sandbox configuration file to run a logon command to swap the mouse setting.

In this example, the `C:\sandbox` folder on the host is mapped to the `C:\sandbox` folder in the sandbox, so the `SwapMouse.ps1` script can be referenced in the sandbox configuration file.

### SwapMouse.ps1

Create a PowerShell script using the following code, and save it in the `C:\sandbox` directory as `SwapMouse.ps1`.

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Windows.Forms") | Out-Null

$SwapButtons = Add-Type -MemberDefinition @'
[DllImport("user32.dll")]
public static extern bool SwapMouseButton(bool swap);
'@ -Name "NativeMethods" -Namespace "PInvoke" -PassThru

$SwapButtons::SwapMouseButton(!([System.Windows.Forms.SystemInformation]::MouseButtonsSwapped))
```

### SwapMouse.wsb

```xml
<Configuration>
  <MappedFolders>
    <MappedFolder>
      <HostFolder>C:\sandbox</HostFolder>
      <SandboxFolder>C:\sandbox</SandboxFolder>
      <ReadOnly>True</ReadOnly>
    </MappedFolder>
  </MappedFolders>
  <LogonCommand>
    <Command>powershell.exe -ExecutionPolicy Bypass -File C:\sandbox\SwapMouse.ps1</Command>
  </LogonCommand>
</Configuration>
```