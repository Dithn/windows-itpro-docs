---
title: Configure Shell Launcher
description: Learn how to configure Shell Launcher.
ms.date: 3/7/2025
ms.topic: how-to
---

# Configure Shell Launcher

There are two ways you can configure Shell Launcher:

1. Using the `ShellLauncher` node of the [Assigned Access Configuration Service Provider (CSP)](/windows/client-management/mdm/assignedaccess-csp), which also automatically enables Shell Launcher on the device, if the device supports it
1. Using the **Shell Launcher WMI providers** directly in an application. When using this method, you must [enable Shell Launcher](#enable-shell-launcher) first

You can configure the following options for Shell Launcher:

- Add/remove a shell configuration for a specific user or group
- Change the default shell configuration
- Get information on a shell configuration for a specific user or group

> [!NOTE]
> Any changes don't take effect until a user signs in.

## Enable Shell Launcher

Shell Launcher is an optional component in Windows that is not enabled by default. To configure it, you must first enable it. You can enable and configure Shell Launcher in a customized Windows image, or you can enable it before applying a provisioning package to configure it.

> [!NOTE]
> When you configure Shell Launcher with the Assigned Access Configuration Service Provider (CSP), Shell Launcher is automatically enabled, if the device supports it. There's no need to enable Shell Launcher separately when you configure it using Assigned Access CSP.

There are multiple ways to enable Shell Launcher, select the method that best fits your needs to learn more.

#### [:::image type="icon" source="../images/icons/control-panel.svg"::: **Control Panel**](#tab/control-panel1)

To enable Shell Launcher using Control Panel, follow these steps:

1. Open **Control Panel** > **Programs** > **Turn Windows features on or off** or use the command `optionalfeatures.exe`
1. Expand **Device Lockdown** and select **Shell Launcher**
1. Select **OK** to enable Shell Launcher

#### [:::image type="icon" source="../images/icons/powershell.svg"::: **PowerShell**](#tab/powershell1)

To enable Shell Launcher using PowerShell, follow these steps:

1. Open a PowerShell window with administrator privileges
1. Run the following command:

    ```powershell
    Enable-WindowsOptionalFeature -FeatureName Client-DeviceLockdown,Client-EmbeddedShellLauncher -Online
    ```

#### [:::image type="icon" source="../images/icons/settings.svg"::: **DISM**](#tab/dism1)

The following example uses a Windows image called `install.wim`, but you can use the same procedure to apply a provisioning package.

1. Open a command prompt with administrator privileges.
1. Copy install.wim to a temporary folder on hard drive (in the following steps, we assume it's called `C:\wim`)
1. Modify the following script to match your environment:

```cmd
@echo off
REM Create a new directory
md c:\wim

REM Mount the image
dism /mount-wim /wimfile:c:\bootmedia\sources\install.wim /index:1 /MountDir:c:\wim

REM Enable the feature
dism /image:c:\wim /enable-feature /all /featureName:Client-EmbeddedShellLauncher

REM Commit the change
dism /unmount-wim /MountDir:c:\wim /Commit
```

For more information on DISM, see [What Is Deployment Image Servicing and Management](/windows-hardware/manufacture/desktop/what-is-dism).

#### [:::image type="icon" source="../images/icons/dev.svg"::: **WMI**](#tab/wmi)

You can enable or disable Shell Launcher by calling the `SetEnabled` function in the Windows Management Instrumentation (WMI) class `WESL_UserSetting`.

For more information, see [WESL_UserSetting](wesl-usersetting.md).

---

## Launch different shells for different user accounts

By default, Shell Launcher runs the default shell, which is specified when you create the OS image at design time. The default shell is set to the Windows Command Processor (`Cmd.exe`), but you can specify any executable file to be the default shell.

You can also configure Shell Launcher to launch a different shell for specific users or groups if you don't want to run the default shell. For example, you might configure a device to launch a custom application shell for guest accounts, but run the standard Windows Explorer shell for administrator accounts for servicing the device.

When the current signed in account belongs to two or more groups that have different configurations defined for each group, Shell Launcher uses the first configuration it finds. The search order isn't defined, so we recommend that you avoid assigning a user to multiple groups with different Shell Launcher configurations.

> [!NOTE]
> If you use the WMI provider to configure Shell Launcher for a user or group at run time, you must use the security identifier (SID) for that security principal. You can't use the user name or group name.
>
> For more information about common security identifiers, see [Well-known SIDs](/windows/win32/secauthz/well-known-sids).

## Shell Launcher startup and exit behavior

Shell Launcher processes the `Run` and `RunOnce` registry keys before starting the custom shell, so your custom shell doesn't need to handle the automatic startup of other applications and services.

Shell Launcher also handles the behavior of the system when your custom shell exits. You can configure the shell exit behavior if the default behavior doesn't meet your needs. When a custom shell exits, Shell Launcher can perform one of four actions:

- `0`: Restart the shell
- `1`: Restart the device
- `2`: Shut down the device
- `3`: Do nothing

> [!IMPORTANT]
> Make sure that your shell application does not automatically exit and is not automatically closed by any features such as Dialog Filter, as this can lead to an infinite cycle of exiting and restarting, unless the return code action is set to do nothing.

### Default return code action

You can define a default return code action for Shell Launcher with the DefaultReturnCodeAction setting. If you don't change the initial value, the default return code action is set to 0 (zero), which indicates that Shell Launcher restarts the shell when the shell exits.

### Map the exit code to a Shell Launcher action

Shell Launcher can take a specific action based on the exit code returned by the shell. For any given exit code returned by the shell, you can configure the action that Shell Launcher takes by mapping that exit code to one of the shell exit actions.

If the exit code doesn't match a defined value, Shell Launcher performs the default return code action.

For example, your shell might return exit code values of `-1`, `0`, `1`, or `255` depending on how the shell exits. You can configure Shell Launcher to:

- restart the device (`1`) when the shell returns an exit code of value `-1`
- restart the shell (`0`) when the shell returns an exit code of value `0`
- do nothing (`3`) when the shell returns an exit code of value 1
- shut down the device (`2`) when the shell returns an exit code of value `255`

Your custom return code action mapping would look like this:

|Exit code|Action|
|:----:|----|
|`-1`|`1` (restart the device)|
|`0`|`0` (restart the shell)|
|`1`|`3` (do nothing)|
|`255`|`2` (shut down the device)|

## Set your custom shell with the Assigned Access CSP

The configuration of Shell Launcher is done using an XML file. The XML file is applied to the device via the [Assigned Access CSP](/windows/client-management/mdm/assignedaccess-csp#shelllauncher), using one of the following options:

- A Mobile Device Management (MDM) solution, like Microsoft Intune
- Provisioning packages
- The MDM Bridge WMI Provider

> [!NOTE]
> Configuring Shell Launcher using Assigned Access CSP, automatically enables Shell Launcher on the device, if the device supports it.

To learn how to configure the Shell Launcher XML file, see [Create a Shell Launcher configuration file](configuration-file.md).

[!INCLUDE [tab-intro](../../../includes/configure/tab-intro.md)]

#### [:::image type="icon" source="../images/icons/intune.svg"::: **Intune**](#tab/intune)

You can configure devices using a [custom policy][MEM-1] with the [AssignedAccess CSP][WIN-3].

- **Setting:** `./Vendor/MSFT/AssignedAccess/ShellLauncher`
- **Value:** content of the XML configuration file

Assign the policy to a group that contains as members the devices that you want to configure.

#### [:::image type="icon" source="../images/icons/csp.svg"::: **CSP**](#tab/csp)

You can configure devices using the [AssignedAccess CSP][WIN-3].

- **Setting:** `./Vendor/MSFT/AssignedAccess/ShellLauncher`
- **Value:** content of the XML configuration file

#### [:::image type="icon" source="../images/icons/provisioning-package.svg"::: **PPKG**](#tab/ppkg)

You can configure Shell Launcher by creating a provisioning package and then applying the provisioning package during image deployment time or at runtime:

- If you're creating an installation media with settings for Shell Launcher included in the image, or you're applying a provisioning package during setup, you must enable Shell Launcher on the installation media with DISM for a provisioning package to successfully apply
- If executing the provisioning package at runtime, ensure to [enable Shell Launcher](#enable-shell-launcher) before applying the provisioning package

[!INCLUDE [provisioning-package-1](../../../includes/configure/provisioning-package-1.md)]

| Path | Setting name | Value |
|--|--|--|
| `SMISettings/ShellLauncher/` | `Enable` | ENABLE |
| `SMISettings/ShellLauncher/` | * | It depends on specific settings. |

[!INCLUDE [provisioning-package-2](../../../includes/configure/provisioning-package-2.md)]

#### [:::image type="icon" source="../images/icons/powershell.svg"::: **PowerShell**](#tab/ps)

[!INCLUDE [powershell-wmi-bridge-1](../../../includes/configure/powershell-wmi-bridge-1.md)]

```PowerShell
$shellLauncherConfiguration = @"

# content of the XML configuration file

"@

$namespaceName="root\cimv2\mdm\dmmap"
$className="MDM_AssignedAccess"
$obj = Get-CimInstance -Namespace $namespaceName -ClassName $className
$obj.ShellLauncher = [System.Net.WebUtility]::HtmlEncode($shellLauncherConfiguration)
$obj = Set-CimInstance -CimInstance $obj -ErrorVariable cimSetError -ErrorAction SilentlyContinue
if($cimSetError) {
    Write-Output "An ERROR occurred. Displaying error record and attempting to retrieve error logs...`n"
    Write-Error -ErrorRecord $cimSetError[0]

    $timeout = New-TimeSpan -Seconds 30
    $stopwatch = [System.Diagnostics.Stopwatch]::StartNew()
    $eventLogFilterHashTable = @{ LogName='Microsoft-Windows-AssignedAccess/Admin' }
    do{
        $events = Get-WinEvent -FilterHashtable $eventLogFilterHashTable -ErrorAction Ignore
    } until ($events.Count -or $stopwatch.Elapsed -gt $timeout) # wait for the log to be available

    if($events.Count) {
        $events | ForEach-Object {
            Write-Output "$($_.TimeCreated) [$($_.LevelDisplayName.ToUpper())] $($_.Message -replace "`n|`r")"
        }
    } else {
        Write-Warning "Timed-out attempting to retrieve event logs..."
    }

    Exit 1
}

Write-Output "Successfully applied Shell Launcher configuration"
```

[!INCLUDE [powershell-wmi-bridge-2](../../../includes/configure/powershell-wmi-bridge-2.md)]

---

> [!TIP]
> For practical examples, see the [Quickstart: configure a kiosk experience with Shell Launcher](quickstart-kiosk.md).

## User experience

After the settings are applied, the users that are configured to use Shell Launcher will execute the custom shell after sign-in.

Depending on your configuration, you can have a user to automatically sign in to the device.

## Remove Shell Launcher

Here are the options to remove Shell Launcher, select the method that best fits your needs:

#### [:::image type="icon" source="../images/icons/intune.svg"::: **Intune**](#tab/intune)

Unassign or delete the policy that contains the configuration.

#### [:::image type="icon" source="../images/icons/csp.svg"::: **CSP**](#tab/csp)

Unassign or delete the policy that contains the configuration.

#### [:::image type="icon" source="../images/icons/provisioning-package.svg"::: **PPKG**](#tab/ppkg)

Uninstall the provisioning package that contains the configuration.

#### [:::image type="icon" source="../images/icons/powershell.svg"::: **PowerShell**](#tab/ps)

```PowerShell
$namespaceName="root\cimv2\mdm\dmmap"
$className="MDM_AssignedAccess"
$obj = Get-CimInstance -Namespace $namespaceName -ClassName $className
$obj.Configuration = $null
Set-CimInstance -CimInstance $obj
```

---

## Next steps

> [!div class="nextstepaction"]
> Learn how to configure the Shell Launcher XML file:
>
> [Create a Shell Launcher configuration file](configuration-file.md)

<!--links-->

[MEM-1]: /mem/intune/configuration/custom-settings-windows-10
[WIN-3]: /windows/client-management/mdm/assignedaccess-csp
