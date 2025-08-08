---
title: WEKF_PredefinedKey.Enable
description: WEKF_PredefinedKey.Enable
ms.date: 01/13/2025
ms.topic: reference
---

# WEKF_PredefinedKey.Enable

[!INCLUDE [supported-os-enterprise-plus](../../../includes/iot/supported-os-enterprise-plus.md)]

This method blocks the specified predefined key combination.

## Syntax

```powershell
[Static] uint32 Enable(
    [In] string PredefinedKey
);
```

## Parameters

**PredefinedKey**</br>The predefined key combination to block. For a list of predefined keys, see [Predefined key combinations](predefined-key-combinations.md).

## Return Value

Returns an HRESULT value that indicates [WMI non-error constant](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Related articles

- [WEKF_PredefinedKey](wekf-predefinedkey.md)
- [Keyboard Filter](index.md)
