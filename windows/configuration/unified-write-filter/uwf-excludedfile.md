---
title: UWF_ExcludedFile
description: UWF_ExcludedFile
ms.date: 05/20/2024
ms.topic: reference
---

# UWF_ExcludedFile

Contains the files and folders that are currently in the file exclusion list for a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
class UWF_ExcludedFile {
    [Read] string FileName;
};
```

## Members

The following tables list any methods and properties that belong to this class.

### Properties

| Property | Data&nbsp;type | Qualifier | Description |
|----------|-----------|-----------|-------------|
| FileName | string | [read] | The name of the file or folder path in the file exclusion list, including the full path relative to the volume. |

### Remarks

UWF_ExcludedFile does not represent an actual WMI object, and you cannot use this class to get or set file exclusions.

You must use the [UWF_Volume.GetExclusions](uwf-volumegetexclusions.md) method to retrieve UWF_ExcludedFile objects.

You can use the [UWF_Volume.AddExclusion](uwf-volumeaddexclusion.md) and [UWF_Volume.RemoveExclusion](uwf-volumeremoveexclusion.md) methods to add or remove file and folder exclusions to a volume.

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
