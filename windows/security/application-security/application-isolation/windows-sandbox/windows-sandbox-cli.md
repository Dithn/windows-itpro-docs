---
title: Windows Sandbox command line
description: Windows Sandbox command line interface
ms.topic: how-to
ms.date: 10/22/2024
---

# Windows Sandbox command line interface

Starting with Windows 11, version 24H2, the Windows Command Line Interface (CLI) offers powerful tools for creating, managing, and controlling sandboxes, executing commands, and sharing folders within sandbox sessions. This functionality is especially valuable for scripting, task automation, and improving development workflows. In this section, you'll explore how the Windows Sandbox CLI operates, with examples demonstrating how to use each command to enhance your development process.

**Common parameters**:

- `--raw`: Formats all outputs in JSON format.
- `-?, -h, --help`: Show help and usage information

## Start

The start command creates and launches a new sandbox. The command returns the sandbox ID, which is a unique identifier for the sandbox. The sandbox ID can be used to refer to the sandbox in other commands.

- `--id <id>`:  ID of the Windows Sandbox environment.
- `--c, --config <config>`: Formatted string with the settings that should be used to create the Windows Sandbox environment.

**Examples**:

- Create a Windows Sandbox environment with the default settings:

    ```cmd
    wsb start
    ```

- Create a Windows Sandbox environment with a custom configuration:

    ```cmd
    wsb start --config "<Configuration><Networking>Disabled</Networking></Configuration>"
    ```

## List

The list command displays a table that shows the information the running Windows Sandbox sessions for the current user. The table includes the sandbox ID. The status can be either running or stopped. The uptime is the duration that the sandbox has been running.

```cmd
wsb list
```

## Exec

The exec command executes a command in the sandbox. The command takes two arguments: the sandbox ID and the command to execute. The command can be either a built-in command or an executable file. The exec command runs the command in the sandbox and returns the exit code. The exec command can also take optional arguments that are passed to the process started in the sandbox.

> [!NOTE]
> Currently, there is no support for process I/O meaning that there is no way to retrieve the output of a command run in Sandbox.

An active user session is required to execute a command in the context of the currently logged on user. Therefore, before running this command a remote desktop connection should be established. This can be done using the [connect](#connect) command.

- `--id <id>` (REQUIRED): ID of the Windows Sandbox environment.
- `-c, --command <command>` (REQUIRED): The command to execute within Windows Sandbox.
- `-r, --run-as <ExistingLogin|System>` (REQUIRED): Specifies the user context to execute the command within. If the System option is selected, the command runs in the system context. If the ExistingLogin option is selected, the command runs in the currently active user session or fails if there's no active user session.
- `-d, --working-directory <directory>`: Directory to execute command in.

```cmd
wsb exec –-id 12345678-1234-1234-1234-1234567890AB -c app.exe -r System
```

## Stop

The stop command stops a running Windows Sandbox session. The command takes the sandbox ID as an argument.

The stop command terminates the sandbox process and releases the resources allocated to the sandbox. The stop command also closes the window that shows the sandbox desktop.

```cmd
wsb stop --id 12345678-1234-1234-1234-1234567890AB
```

## Share

The share command shares a host folder with the sandbox. The command takes three arguments: the sandbox ID, the host path, and the sandbox path. The host path should be a folder. The sandbox path can be either an existing or a new folder. An Additional, `--allow-write` option can be used to allow or disallow the Windows Sandbox environment to write to the folder.

- `--id <id>` (REQUIRED): ID of the Windows Sandbox environment.
- `-f, --host-path <host-path>` (REQUIRED): Path to folder that is shared from the host.
- `-s, --sandbox-path <sandbox-path>` (REQUIRED): Path to the folder within the Windows Sandbox.
- `-w, --allow-write`: If specified, the Windows Sandbox environment is allowed to write to the shared folder.

```cmd
wsb share --id 12345678-1234-1234-1234-1234567890AB -f C:\host\folder -s C:\sandbox\folder --allow-write
```

## Connect

The connect command starts a remote session within the sandbox. The command takes the sandbox ID as an argument. The connect command opens a new window with a remote desktop session. The connect command allows the user to interact with the sandbox using the mouse and keyboard.

```cmd
wsb connect --id 12345678-1234-1234-1234-1234567890AB
```

## IP

The ip command displays the IP address of the sandbox. The command takes the sandbox ID as an argument.

```cmd
wsb ip --id 12345678-1234-1234-1234-1234567890AB
```
