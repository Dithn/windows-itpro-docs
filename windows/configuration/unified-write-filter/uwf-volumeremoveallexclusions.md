---
title: UWF_Volume.RemoveAllExclusions
description: UWF_Volume.RemoveAllExclusions
ms.date: 05/20/2024
ms.topic: reference
---

# UWF_Volume.RemoveAllExclusions

Removes all files and folders from the file exclusion list for a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
UInt32 RemoveAllExclusions();
```

## Parameters

None.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI errorj constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

This command does not remove registry exclusions.

You must use an administrator account to remove file or folder exclusions, and you must restart the device for this change to take effect.

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
