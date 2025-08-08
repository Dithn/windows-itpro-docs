---
author: paolomatarazzo
ms.author: paoloma
ms.date: 04/03/2025
ms.topic: include
---

### Remove Quick Settings

This policy setting removes Quick Settings from the taskbar. Quick Settings is located in the system tray area, and includes icons for current network and volume.

If this setting is enabled, Quick Settings isn't displayed in the system tray area.

> [!NOTE]
> A reboot is required for this policy setting to take effect.

|  | Path |
|--|--|
| **CSP** | - `./User/Vendor/MSFT/Policy/Config/Start/`[DisableControlCenter](/windows/client-management/mdm/policy-csp-start#disablecontrolcenter) |
| **GPO** | - **User Configuration** > **Administrative Templates** > **Start Menu and Taskbar** > **Remove Quick Settings** |
