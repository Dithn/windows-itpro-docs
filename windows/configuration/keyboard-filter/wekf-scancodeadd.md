---
title: WEKF_Scancode.Add
description: WEKF_Scancode.Add
ms.date: 01/13/2025
ms.topic: reference
---

# WEKF_Scancode.Add

[!INCLUDE [supported-os-enterprise-plus](../../../includes/iot/supported-os-enterprise-plus.md)]

This method adds a new custom scan code combination and enables Keyboard Filter to block the new combination.

## Syntax

```powershell
[Static] uint32 Add(
    [In] string Modifiers,
    [In] uint16 Scancode
);
```

## Parameters

**Modifers**</br>The modifier keys that are part of the key combination to block.

**Scancode**</br>The hardware scan code of the key to block.

## Return Value

Returns an HRESULT value that indicates [WMI non-error constant](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

**WEKF_Scancode.Add** creates a new **WEKF_Scancode** object and sets the **Enabled** property of the new object to **true**.

If a **WEKF_Scancode** object already exists with same *Modifiers* and *Scancode* properties, then **WEKF_Scancode.Add** returns an error code and doesn't create a new object or modify any properties of the existing object. If the existing **WEKF_Scancode** object has the **Enabled** property set to **false**, Keyboard Filter doesn't block the scan code.

## Related articles

- [WEKF_Scancode](wekf-scancode.md)
- [Keyboard Filter](index.md)
