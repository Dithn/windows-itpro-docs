---
title: WESL_UserSetting.SetEnabled
description: WESL_UserSetting.SetEnabled
ms.date: 3/7/2025
ms.topic: reference
---

# WESL_UserSetting.SetEnabled

This method enables or disables Shell Launcher.

[!INCLUDE [shell-launcher](../../../includes/licensing/shell-launcher.md)]

## Syntax

```mof
[Static] uint32 SetEnabled(
    [In, Required] boolean Enabled
);
```

## Parameters

**Enabled**<br/>\[in, required\] A Boolean value that indicates whether to enable or disable Shell Launcher.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

This method enables or disables Shell Launcher by modifying the **Shell** value in the registry key `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon`. If Unified Write Filter (UWF) is enabled, you may need to disable UWF or commit this registry key by using [UWF_RegistryFilter.CommitRegistry](../unified-write-filter/uwf-registryfiltercommitregistry.md) in order to enable or disable Shell Launcher.

Enabling or disabling Shell Launcher does not take effect until a user signs in.
