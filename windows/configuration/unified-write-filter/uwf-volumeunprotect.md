---
title: UWF_Volume.Unprotect
description: UWF_Volume.Unprotect
ms.date: 05/20/2024
ms.topic: reference
---

# UWF_Volume.Unprotect

Disables UWF protection of the volume after the next system restart.

## Syntax

```powershell
UInt32 Unprotect();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

Unprotecting the volume does not remove the [UWF_Volume](uwf-volume.md) entry or any configuration settings from the UWF configuration registry. This means that you can unprotect a volume, and then protect it again later, while keeping any file exclusions or volume configurations that you have defined.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related articles

- [UWF_Volume](uwf-volume.md)
- [Unified Write Filter]( index.md)
