---
title: UWF_OverlayFile
description: UWF_OverlayFile
ms.date: 05/20/2024
ms.topic: reference
---

# UWF_OverlayFile

Contains a file that is currently in the overlay for a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
class UWF_OverlayFile {
    [read] string FileName;
    [read] UInt64 FileSize;
};
```

## Members

The following table lists any properties that belong to this class.

### Properties

| Property | Data&nbsp;type | Qualifier | Description |
|----------|----------------|-----------|-------------|
| FileName | string | [read] | The name of the file in the file overlay. |
| FileSize | UInt64 | [read] | The size of the file in the file overlay. |

### Remarks

You cannot use the **UWF_ OverlayFile** class directly to get overlay files. You must use the **UWF_Overlay.GetOverlayFiles** method to retrieve **UWF_ OverlayFile** objects.

For more information about specific limitations and conditions when using the **GetOverlayFiles** method, see the **Remarks** section in the [UWF_Overlay.GetOverlayFiles](uwf-overlaygetoverlayfiles.md) topic in the UWF WMI provider technical reference.

## Requirements

| Windows Edition        | Supported |
|:-----------------------|:---------:|
| Windows Home           | No        |
| Windows Pro            | No        |
| Windows Enterprise     | Yes       |
| Windows Education      | Yes       |
| Windows IoT Enterprise | Yes       |

## Related articles

- [Unified Write Filter WMI provider reference](uwf-wmi-provider-reference.md)
- [Unified Write Filter]( index.md)
