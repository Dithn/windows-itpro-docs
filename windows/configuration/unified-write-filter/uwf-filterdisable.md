---
title: UWF_Filter.Disable
description: UWF_Filter.Disable
ms.date: 05/20/2024
ms.topic: reference
---

# UWF_Filter.Disable

Disables Unified Write Filter (UWF) on the next restart.

## Syntax

```powershell
UInt32 Disable();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

You must use an administrator account to disable UWF.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related articles

- [UWF_Filter](uwf-filter.md)
- [Unified Write Filter]( index.md)
