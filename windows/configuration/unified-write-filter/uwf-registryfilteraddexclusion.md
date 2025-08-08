---
title: UWF_RegistryFilter.AddExclusion
description: UWF_RegistryFilter.AddExclusion
ms.date: 05/20/2024
ms.topic: reference
---

# UWF_RegistryFilter.AddExclusion

Adds a registry key to the registry exclusion list for Unified Write Filter (UWF).

> [!IMPORTANT]
> Only registry subkeys under the following registry keys can be added to the exclusion list.
>
> - HKEY_LOCAL_MACHINE\BCD00000000
> - HKEY_LOCAL_MACHINE\SYSTEM
> - HKEY_LOCAL_MACHINE\SOFTWARE
> - HKEY_LOCAL_MACHINE\SAM
> - HKEY_LOCAL_MACHINE\SECURITY
> - HKEY_LOCAL_MACHINE\COMPONENTS

> [!IMPORTANT]
> Excluding a registry key from filtering also excludes all subkeys from filtering.

## Syntax

```powershell
UInt32 AddExclusion(
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
