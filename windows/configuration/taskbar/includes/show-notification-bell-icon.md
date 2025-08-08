---
author: paolomatarazzo
ms.author: paoloma
ms.date: 02/25/2025
ms.topic: include
---

### Show notification bell icon

This policy setting allows you to show the notification bell icon in the system tray:

- If you enable this policy setting, the notification icon is always displayed
- If you disable or don't configure this policy setting, the notification icon is only displayed when there's a special status (for example, when *do not disturb* is turned on)

> [!NOTE]
> A reboot is required for this policy setting to take effect.

|  | Path |
|--|--|
| **CSP** |- `./User/Vendor/MSFT/Policy/Config/Start/`[AlwaysShowNotificationIcon](/windows/client-management/mdm/policy-csp-start#AlwaysShowNotificationIcon) |
| **GPO** |- **User Configuration** > **Administrative Templates** > **Start Menu and Taskbar** > **Show notification bell icon** |
