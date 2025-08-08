---
title: UWF_RegistryFilter.GetExclusions
description: UWF_RegistryFilter.GetExclusions
ms.date: 05/20/2024
ms.topic: reference
---

# UWF_RegistryFilter.GetExclusions

Retrieves all registry key exclusions from a device that is protected by Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 GetExclusions(
    [out, EmbeddedInstance("UWF_ExcludedRegistryKey")] string ExcludedKeys[]
);
```

## Parameters

**ExcludedKeys**</br>\[out\] An array of [UWF_ExcludedRegistryKey](uwf-excludedregistrykey.md) objects that represent the registry keys excluded from UWF filtering.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

If this method does not find any registry keys in the registry key exclusion list, it sets the *ExcludedKeys* parameter to null.

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
