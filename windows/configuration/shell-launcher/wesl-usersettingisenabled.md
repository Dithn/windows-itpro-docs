---
title: WESL_UserSetting.IsEnabled
description: WESL_UserSetting.IsEnabled
ms.date: 3/7/2025
ms.topic: reference
---

# WESL_UserSetting.IsEnabled

This method retrieves a value that indicates if Shell Launcher is enabled or disabled.

[!INCLUDE [shell-launcher](../../../includes/licensing/shell-launcher.md)]

## Syntax

```mof
[Static] uint32 IsEnabled(
    [Out, Required] boolean Enabled
);
```

## Parameters

**Enabled**<br/>\[out, required\] A Boolean value that indicates if Shell Launcher is enabled.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).
