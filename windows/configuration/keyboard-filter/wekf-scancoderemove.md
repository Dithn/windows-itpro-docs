---
title: WEKF_Scancode.Remove
description: WEKF_Scancode.Remove
ms.date: 01/13/2025
ms.topic: reference
---

# WEKF_Scancode.Remove

[!INCLUDE [supported-os-enterprise-plus](../../../includes/iot/supported-os-enterprise-plus.md)]

This method removes a custom scan code key combination, causing Keyboard Filter to stop blocking the removed combination.

## Syntax

```powershell
[Static] uint32 Remove(
    [In] string Modifiers,
    [In] uint16 Scancode
);
```

## Parameters

**Modifiers**</br>The modifier keys of the combination to remove.

**Scancode**</br>The scan code of the combination to remove.

## Return Value

Returns an HRESULT value that indicates [WMI non-error constant](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error constant](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

**WEKF_Scancode.Remove** removes an existing **WEKF_Scancode** object. If the object doesn't exist, **WEKF_Scancode.Remove** returns an error with the value 0x8007007B.

Because this method is static, you can't call it on an object instance, but must instead call it at the class level.

## Related articles

- [WEKF_Scancode](wekf-scancode.md)
- [Keyboard Filter](index.md)
