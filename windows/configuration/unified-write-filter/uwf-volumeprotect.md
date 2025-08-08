---
title: UWF_Volume.Protect
description: UWF_Volume.Protect
ms.date: 05/20/2024
ms.topic: reference
---

# UWF_Volume.Protect

Enables Unified Write Filter (UWF) to protect the volume after the next system restart, if UWF is enabled after the restart.

## Syntax

```powershell
UInt32 Protect();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

UWF starts protecting the volume after the next device restart in which UWF is enabled.

This method does not enable UWF if it is disabled; you must explicitly enable UWF for the next session to start volume protection.

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
