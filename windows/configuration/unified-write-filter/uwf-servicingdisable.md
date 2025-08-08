---
title: UWF_Servicing.Disable
description: UWF_Servicing.Disable
ms.date: 05/20/2024
ms.topic: reference
---

# UWF_Servicing.Disable

Disables Unified Write Filter (UWF) servicing mode.

## Syntax

```powershell
UInt32 Disable();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

When this method is called, the system will leave servicing mode in the next session after a restart.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related articles

- [UWF_Servicing](uwf-servicing.md)
- [Unified Write Filter]( index.md)
