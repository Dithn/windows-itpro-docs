---
title: WindowsBackupAndRestore CSP
description: Learn more about the WindowsBackupAndRestore CSP.
ms.date: 04/30/2025
ms.topic: generated-reference
---

<!-- Auto-Generated CSP Document -->

<!-- WindowsBackupAndRestore-Begin -->
# WindowsBackupAndRestore CSP

[!INCLUDE [Windows Insider tip](includes/mdm-insider-csp-note.md)]

<!-- WindowsBackupAndRestore-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- WindowsBackupAndRestore-Editable-End -->

<!-- WindowsBackupAndRestore-Tree-Begin -->
The following list shows the WindowsBackupAndRestore configuration service provider nodes:

- ./Device/Vendor/MSFT/WindowsBackupAndRestore
  - [EnableWindowsRestore](#enablewindowsrestore)
<!-- WindowsBackupAndRestore-Tree-End -->

<!-- Device-EnableWindowsRestore-Begin -->
## EnableWindowsRestore

<!-- Device-EnableWindowsRestore-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-EnableWindowsRestore-Applicability-End -->

<!-- Device-EnableWindowsRestore-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WindowsBackupAndRestore/EnableWindowsRestore
```
<!-- Device-EnableWindowsRestore-OmaUri-End -->

<!-- Device-EnableWindowsRestore-Description-Begin -->
<!-- Description-Source-DDF -->
Sets a policy to enable Windows Restore.
<!-- Device-EnableWindowsRestore-Description-End -->

<!-- Device-EnableWindowsRestore-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-EnableWindowsRestore-Editable-End -->

<!-- Device-EnableWindowsRestore-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `bool` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | false |
<!-- Device-EnableWindowsRestore-DFProperties-End -->

<!-- Device-EnableWindowsRestore-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| false (Default) | Windows Restore Not Configured. |
| true | Windows Restore Enabled. |
<!-- Device-EnableWindowsRestore-AllowedValues-End -->

<!-- Device-EnableWindowsRestore-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-EnableWindowsRestore-Examples-End -->

<!-- Device-EnableWindowsRestore-End -->

<!-- WindowsBackupAndRestore-CspMoreInfo-Begin -->
<!-- Add any additional information about this CSP here. Anything outside this section will get overwritten. -->
<!-- WindowsBackupAndRestore-CspMoreInfo-End -->

<!-- WindowsBackupAndRestore-End -->

## Related articles

[Configuration service provider reference](configuration-service-provider-reference.md)
