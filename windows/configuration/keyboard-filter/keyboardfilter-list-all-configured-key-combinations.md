---
title: List all configured key combinations
description: List all configured key combinations
ms.date: 01/13/2025
ms.topic: reference
---

# List all configured key combinations

[!INCLUDE [supported-os-enterprise-plus](../../../includes/iot/supported-os-enterprise-plus.md)]

The following sample Windows PowerShell script uses the Windows Management Instrumentation (WMI) providers for Keyboard Filter to displays all key combination configurations for Keyboard Filter.

## List-rules.ps1

```powershell
#
# Copyright (C) Microsoft. All rights reserved.
#

<#
.Synopsis
    Enumerate all active keyboard filter rules on the system.
.Description
    For each instance of WEKF_PredefinedKey, WEKF_CustomKey, and WEKF_Scancode,
    get the Enabled property.  If Enabled, then output a short description
    of the rule.
.Parameter ComputerName
    Optional parameter to specify the remote machine that this script should
    manage.  If not specified, the script will execute all WMI operations
    locally.
#>
param (
    [String] $ComputerName
)

$CommonParams = @{"namespace"="root\standardcimv2\embedded"}
$CommonParams += $PSBoundParameters

write-host Enabled Predefined Keys -foregroundcolor cyan
Get-WMIObject -class WEKF_PredefinedKey @CommonParams |
    foreach {
        if ($_.Enabled) {
            write-host $_.Id
        }
    }

write-host Enabled Custom Keys -foregroundcolor cyan
Get-WMIObject -class WEKF_CustomKey @CommonParams |
    foreach {
        if ($_.Enabled) {
            write-host $_.Id
        }
    }

write-host Enabled Scancodes -foregroundcolor cyan
Get-WMIObject -class WEKF_Scancode @CommonParams |
    foreach {
        if ($_.Enabled) {
            "{0}+{1:X4}" -f $_.Modifiers, $_.Scancode
        }
    }
```

## Related articles

[Windows PowerShell script samples for keyboard filter](keyboardfilter-powershell-script-samples.md)

[Keyboard filter WMI provider reference](keyboardfilter-wmi-provider-reference.md)

[Keyboard filter](index.md)
