---
title: WESL_UserSetting.GetDefaultShell
description: WESL_UserSetting.GetDefaultShell
ms.date: 3/7/2025
ms.topic: reference
---

# WESL_UserSetting.GetDefaultShell

This method retrieves the default Shell Launcher configuration.

[!INCLUDE [shell-launcher](../../../includes/licensing/shell-launcher.md)]

## Syntax

```mof
[Static] uint32 GetDefaultShell (
    [Out, Required] string Shell,
    [Out, Required] sint32 DefaultAction
);
```

## Parameters

**Shell**<br/>\[out, required\] The application or executable that Shell Launcher starts as the shell.

**DefaultAction**<br/>\[out, required\] The default action Shell Launcher takes when the shell application exits.

The possible actions are defined in the following table:

| Value | Description |
|:-----:|-------------|
| 0 | Restart the shell. |
| 1 | Restart the device. |
| 2 | Shut down the device. |
| 3 | Do nothing. |

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

Shell Launcher uses the default configuration when the security identifier (SID) of the user who is currently signed in does not match any custom defined Shell Launcher configurations.
