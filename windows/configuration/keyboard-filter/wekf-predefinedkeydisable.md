---
title: WEKF_PredefinedKey.Disable
description: WEKF_PredefinedKey.Disable
ms.date: 01/13/2025
ms.topic: reference
---

# WEKF_PredefinedKey.Disable

[!INCLUDE [supported-os-enterprise-plus](../../../includes/iot/supported-os-enterprise-plus.md)]

Unblocks the specified predefined key combination.

## Syntax

```powershell
[Static] uint32 Disable(
    [In] string PredefinedKey
);
```

## Parameters

**PredefinedKey**</br>\[in\] The predefined key combination to unblock. For a list of predefined keys, see [Predefined key combinations](predefined-key-combinations.md).

## Return Value

Returns an HRESULT value that indicates [WMI Non-error constant](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).


## Related articles

- [WEKF_PredefinedKey](wekf-predefinedkey.md)
- [Keyboard Filter](index.md)
