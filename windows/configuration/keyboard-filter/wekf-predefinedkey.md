---
title: WEKF_PredefinedKey
description: WEKF_PredefinedKey
ms.date: 01/13/2025
ms.topic: reference
---

# WEKF_PredefinedKey

[!INCLUDE [supported-os-enterprise-plus](../../../includes/iot/supported-os-enterprise-plus.md)]

This class blocks or unblocks predefined key combinations, such as Ctrl+Alt+Delete.

## Syntax

```powershell
class WEKF_PredefinedKey {
    [Static] uint32 Enable (
        [In] string PredefinedKey
    );
    [Static] uint32 Disable (
        [In] string PredefinedKey
    );

    [Key] string Id;
    [Read, Write] boolean Enabled;
};
```

## Members

The following tables list any constructors, methods, fields, and properties that belong to this class.

### Methods

| Methods                                                    | Description                            |
|:-----------------------------------------------------------|:---------------------------------------|
| [WEKF_PredefinedKey.Enable](wekf-predefinedkeyenable.md)   | Blocks the specified predefined key.   |
| [WEKF_PredefinedKey.Disable](wekf-predefinedkeydisable.md) | Unblocks the specified predefined key. |

### Properties

| Property    | Data type | Qualifiers    | Description                                                                                                                                                           |
|:------------|:----------|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Id**      | string    | [key]         | The name of the predefined key combination.                                                                                                                           |
| **Enabled** | Boolean   | [read, write] | Indicates whether the key is blocked or unblocked. To indicate that the key is blocked, specify **true**. To indicate that the key isn't blocked, specify **false**. |

### Remarks

All accounts have read access to the **WEKF_PRedefinedKey** class, but only administrator accounts can modify the class.

For a list of predefined key combinations for Keyboard Filter, see [Predefined key combinations](predefined-key-combinations.md).

## Example

The following sample Windows PowerShell script blocks the Ctrl+Alt+Delete and the Ctrl+Esc key combinations when the Keyboard Filter service is running.

```powershell
<#
.Synopsis
    This script shows how to use the built in WMI providers to enable and add
    Keyboard Filter rules through Windows PowerShell on the local computer.
.Parameter ComputerName
    Optional parameter to specify a remote machine that this script should
    manage.  If not specified, the script will execute all WMI operations
    locally.
#>
param (
    [String] $ComputerName
)

$CommonParams = @{"namespace"="root\standardcimv2\embedded"}
$CommonParams += $PSBoundParameters

function Enable-Predefined-Key($Id) {
    <#
    .Synposis
        Toggle on a Predefined Key Keyboard Filter Rule
    .Description
        Use Get-WMIObject to enumerate all WEKF_PredefinedKey instances,
        filter against key value "Id", and set that instance's "Enabled"
        property to 1/true.
    .Example
        Enable-Predefined-Key "Ctrl+Alt+Delete"

        Enable CAD filtering
#>

    $predefined = Get-WMIObject -class WEKF_PredefinedKey @CommonParams |
        where {
            $_.Id -eq "$Id"
        };

    if ($predefined) {
        $predefined.Enabled = 1;
        $predefined.Put() | Out-Null;
        Write-Host Enabled $Id
    } else {
        Write-Error $Id is not a valid predefined key
    }
}

# Some example uses of the function defined above.

Enable-Predefined-Key "Ctrl+Alt+Delete"
Enable-Predefined-Key "Ctrl+Esc"
```

## Related articles

- [Keyboard Filter WMI provider reference](keyboardfilter-wmi-provider-reference.md)
- [Keyboard Filter](index.md)
