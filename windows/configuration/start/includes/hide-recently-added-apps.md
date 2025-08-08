---
author: paolomatarazzo
ms.author: paoloma
ms.date: 02/25/2025
ms.topic: include
---

### Hide recently added apps

With this policy setting, you can prevent the Start menu from displaying a list of recently installed applications:

- If **enabled**, the Start menu doesn't display the **Recently added** list. The corresponding option in Settings can't be configured (grayed out)
- If **disabled** or **not configured**, the Start menu displays the **Recently added** list. The corresponding option in Settings can be configured

|  | Path |
|--|--|
| **CSP** | - `./Device/Vendor/MSFT/Policy/Config/Start/`[HideRecentlyAddedApps](/windows/client-management/mdm/policy-csp-start#hiderecentlyaddedapps)<br>- `./User/Vendor/MSFT/Policy/Config/Start/`[HideRecentlyAddedApps](/windows/client-management/mdm/policy-csp-start#hiderecentlyaddedapps) |
| **GPO** | - **Computer Configuration** > **Administrative Templates** > **Start Menu and Taskbar**<br> - **User Configuration** > **Administrative Templates** > **Start Menu and Taskbar** > **Remove "Recently added" list from Start Menu** |
