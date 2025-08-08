---
title: UWF_RegistryFilter.RemoveExclusion
description: UWF_RegistryFilter.RemoveExclusion
ms.date: 05/20/2024
ms.topic: reference
---

# UWF_RegistryFilter.RemoveExclusion

Removes a registry key from the registry exclusion list for Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 RemoveExclusion(
    string RegistryKey
);
```

## Parameters

**RegistryKey**</br>A string that contains the full path of the registry key.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

You must restart the device before the registry key is excluded from UWF filtering.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related articles

- [UWF_RegistryFilter](uwf-registryfilter.md)
- [Unified Write Filter]( index.md)
