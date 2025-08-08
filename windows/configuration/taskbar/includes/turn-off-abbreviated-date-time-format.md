---
author: paolomatarazzo
ms.author: paoloma
ms.date: 02/25/2025
ms.topic: include
---

### Turn off abbreviated date and time format

This policy setting allows you to show the longer time and date format in the system tray:

- If you enable this policy setting, the time format will include the AM/PM time marker and the date will include the year.

> [!NOTE]
> A reboot is required for this policy setting to take effect.

|  | Path |
|--|--|
| **CSP** |- `./User/Vendor/MSFT/Policy/Config/Start/`[TurnOffAbbreviatedDateTimeFormat](/windows/client-management/mdm/policy-csp-start#TurnOffAbbreviatedDateTimeFormat) |
| **GPO** |- **User Configuration** > **Administrative Templates** > **Start Menu and Taskbar** > **Turn off abbreviated time and date format**|
