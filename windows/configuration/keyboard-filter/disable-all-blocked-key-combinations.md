---
title: Disable all blocked key combinations
description: Disable all blocked key combinations
ms.date: 01/13/2025
ms.topic: reference
---

# Disable all blocked key combinations

[!INCLUDE [supported-os-enterprise-plus](../../../includes/iot/supported-os-enterprise-plus.md)]

The following sample Windows PowerShell script uses the WMI providers to disable all blocked key combinations for Keyboard Filter by using the Windows Management Instrumentation (WMI) providers for Keyboard Filter. The key combination configurations aren't removed, but Keyboard Filter stops blocking any keys.

## Disable-all-rules.ps1

```powershell
#
# Copyright (C) Microsoft. All rights reserved.
#

<#
.Synopsis
    This Windows PowerShell script shows how to enumerate all existing keyboard filter
    rules and how to disable them by setting the Enabled property directly.
.Description
    For each instance of WEKF_PredefinedKey, WEKF_CustomKey, and WEKF_Scancode,
    set the Enabled property to false/0 to disable the filter rule, thus
    allowing all key sequences through the filter.
.Parameter ComputerName
    Optional parameter to specify the remote computer that this script should
    manage.  If not specified, the script will execute all WMI operations
    locally.
#>

param(
    [String]$ComputerName
)

$CommonParams = @{"namespace"="root\standardcimv2\embedded"}
$CommonParams += $PSBoundParameters

Get-WMIObject -class WEKF_PredefinedKey @CommonParams |
    foreach {
        if ($_.Enabled) {
            $_.Enabled = 0;
            $_.Put() | Out-Null;
            Write-Host Disabled $_.Id
        }
    }

Get-WMIObject -class WEKF_CustomKey @CommonParams |
    foreach {
        if ($_.Enabled) {
            $_.Enabled = 0;
            $_.Put() | Out-Null;
            Write-Host Disabled $_.Id
        }
    }

Get-WMIObject -class WEKF_Scancode @CommonParams |
    foreach {
        if ($_.Enabled) {
            $_.Enabled = 0;
            $_.Put() | Out-Null;
            "Disabled {0}+{1:X4}" -f $_.Modifiers,$_.Scancode
        }
    }
```

## Related articles

- [Windows PowerShell script samples for keyboard filter](keyboardfilter-powershell-script-samples.md)
- [Keyboard filter WMI provider reference](keyboardfilter-wmi-provider-reference.md)
- [Keyboard filter](index.md)
