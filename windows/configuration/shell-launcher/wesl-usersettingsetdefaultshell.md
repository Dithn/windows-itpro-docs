---
title: WESL_UserSetting.SetDefaultShell
description: WESL_UserSetting.SetDefaultShell
ms.date: 3/7/2025
ms.topic: reference
---

# WESL_UserSetting.SetDefaultShell

This method sets the default Shell Launcher configuration.

[!INCLUDE [shell-launcher](../../../includes/licensing/shell-launcher.md)]

## Syntax

```mof
[Static] uint32 SetDefaultShell (
    [In, Required] string Shell,
    [In, Required] sint32 DefaultAction
);
```

## Parameters

**Shell**<br/>\[in, required\] The application or executable that Shell Launcher starts as the shell.

**DefaultAction**<br/>\[in, required\] The default action that Shell Launcher takes when the *Shell* application exits.

The possible actions are defined in the following table:

| Value | Description |
|:-------:|-------------|
| 0 | Restart the shell. |
| 1 | Restart the device. |
| 2 | Shut down the device. |
| 3 | Do nothing. |

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

Shell Launcher uses the default configuration when the security identifier (SID) of the user who is currently signed in does not match any custom defined Shell Launcher configurations.
