---
title: UWF_Overlay.SetCriticalThreshold
description: UWF_Overlay.SetCriticalThreshold
ms.date: 05/20/2024
ms.topic: reference
---

# UWF_Overlay.SetCriticalThreshold

Sets the critical threshold for monitoring the size of the Unified Write Filter (UWF) overlay.

## Syntax

```powershell
UInt32 SetCriticalThreshold(
    UInt32 size
);
```

## Parameters

**size**</br>An integer that represents the size, in megabytes, of the critical threshold level for the overlay. If *size* is 0 (zero), UWF does not raise critical threshold events.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

When the size of the overlay reaches or exceeds the *size* threshold value, UWF writes the following notification event to the event log.

| Message ID | Event code | Message text |
|------------|------------|--------------|
| UWF_OVERLAY_REACHED_CRITICAL_LEVEL | 0x80010002L | The UWF overlay size has reached CRITICAL level. |

The critical threshold must be higher than the warning threshold.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related articles

- [UWF_Overlay](uwf-overlay.md)
- [Unified Write Filter]( index.md)
