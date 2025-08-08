---
title: Troubleshooting Unified Write Filter (UWF)
description: Troubleshooting Unified Write Filter (UWF)
ms.date: 05/02/2017
ms.topic: reference
---

# Troubleshooting Unified Write Filter (UWF)

Review the log files and error message information locations for Unified Write Filter (UWF) on your Windows 10 Enterprise device.

If you are having difficulties configuring Unified Write Filter (UWF) on your device, see the following information about how to find event log and error message information for troubleshooting problems with UWF.

## Event logs

UWF uses Windows Event Log to log events, errors and messages.

* Events related to overlay consumption are sent by UWF kernel mode components and are logged in the **Windows Logs\\System** event log.
* Event related to configuration changes and servicing logs are sent by UWF user mode components:
  * Error messages are logged in the **Applications and Services Logs\\Microsoft\\Windows\\UnifiedWriteFilter\\Admin** event log.
  * Informational messages are logged in the **Applications and Services Logs\\Microsoft\\Windows\\UnifiedWriteFilter\\Operational** event log.

## Related articles

[Unified Write Filter]( index.md)

[Common write filter exclusions](uwfexclusions.md)

[Service UWF-protected devices](service-uwf-protected-devices.md)

[Unified Write Filter WMI provider reference](uwf-wmi-provider-reference.md)

[uwfmgr.exe](uwfmgrexe.md)
