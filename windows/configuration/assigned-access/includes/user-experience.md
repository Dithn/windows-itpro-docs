---
author: paolomatarazzo
ms.author: paoloma
ms.date: 3/7/2025
ms.topic: include
---

## User experience

To validate the kiosk configuration, sign in with the user account you specified in the configuration file.

The Assigned Access configuration takes effect the next time the targeted user signs in. If that user account is signed in when you apply the configuration, sign out and sign back in to validate the experience.

### Autotrigger touch keyboard

The touch keyboard is automatically triggered when there's an input needed and no physical keyboard is attached on touch-enabled devices. You don't need to configure any other setting to enforce this behavior.

> [!TIP]
> The touch keyboard is triggered only when tapping a textbox. Mouse clicks don't trigger the touch keyboard. If you're testing this feature, use a physical device instead of a virtual machine (VM), as the touch keyboard isn't triggered on VMs.

### Sign out of assigned access

By default, to exit the kiosk experience, press <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Del</kbd>. The kiosk app exits automatically. If you sign in again as the Assigned Access account, or wait for the sign in screen time-out, the kiosk app relaunches. The default time-out is 30 seconds, but you can change the time-out with the registry key:

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Authentication\LogonUI`

To change the default time for Assigned Access to resume, add *IdleTimeOut* (DWORD) and enter the value data as milliseconds in hexadecimal.

> [!NOTE]
> `IdleTimeOut` doesn't apply to the Microsoft Edge kiosk mode.

The Breakout Sequence of <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Del</kbd> is the default, but this sequence can be configured to be a different sequence of keys. The breakout sequence uses the format **modifiers + keys**. An example breakout sequence is <kbd>CTRL</kbd> + <kbd>ALT</kbd> + <kbd>A</kbd>, where <kbd>CTRL</kbd> + <kbd>ALT</kbd> are the modifiers, and <kbd>A</kbd> is the key value. To learn more, see [Create an Assigned Access configuration XML file](../configuration-file.md).

## Remove Assigned Access

Deleting the Assigned Access configuration removes the policy settings associated with the users, but it can't revert all the changes. For example, in a multi-app kiosk scenario the Start menu configuration is maintained.

#### [:::image type="icon" source="../../images/icons/intune.svg"::: **Intune/CSP**](#tab/intune)

To remove the Assigned Access configuration, unassign or delete the policy that contains the configuration.

#### [:::image type="icon" source="../../images/icons/provisioning-package.svg"::: **PPKG**](#tab/ppkg)

To remove the Assigned Access configuration, uninstall the provisioning package that contains the configuration.

#### [:::image type="icon" source="../../images/icons/powershell.svg"::: **PowerShell**](#tab/ps)

```PowerShell
$namespaceName="root\cimv2\mdm\dmmap"
$className="MDM_AssignedAccess"
$obj = Get-CimInstance -Namespace $namespaceName -ClassName $className
$obj.Configuration = $null
Set-CimInstance -CimInstance $obj
```

#### [:::image type="icon" source="../../images/icons/settings-app.svg"::: **Settings**](#tab/settings)

1. Go to **Settings > Accounts > Other Users**, or use the following shortcut:

    > [!div class="nextstepaction"]
    >
    > [Other Users](ms-settings:otherusers)

1. Select **Kiosk**
1. Under **Kiosk info**, expand the application used for the kiosk experience
1. Select **Remove kiosk**

> [!NOTE]
> This option isn't available using Settings if you configured a restricted user experience.

---

## Next steps

> [!div class="nextstepaction"]
> Review the recommendations before you deploy Assigned Access:
>
> [Assigned Access recommendations](../recommendations.md)
