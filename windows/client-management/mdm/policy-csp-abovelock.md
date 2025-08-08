---
title: AboveLock Policy CSP
description: Learn more about the AboveLock Area in Policy CSP.
ms.date: 06/09/2025
ms.topic: generated-reference
---

<!-- Auto-Generated CSP Document -->

<!-- AboveLock-Begin -->
# Policy CSP - AboveLock

[!INCLUDE [Windows Insider tip](includes/mdm-insider-csp-note.md)]

<!-- AboveLock-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- AboveLock-Editable-End -->

<!-- AllowActionCenterNotifications-Begin -->
## AllowActionCenterNotifications

> [!NOTE]
> This policy is deprecated and may be removed in a future release.

<!-- AllowActionCenterNotifications-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | Not applicable | ✅ Windows 10, version 1507 [10.0.10240] and later |
<!-- AllowActionCenterNotifications-Applicability-End -->

<!-- AllowActionCenterNotifications-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications
```
<!-- AllowActionCenterNotifications-OmaUri-End -->

<!-- AllowActionCenterNotifications-Description-Begin -->
<!-- Description-Source-DDF -->
This policy is deprecated.
<!-- AllowActionCenterNotifications-Description-End -->

<!-- AllowActionCenterNotifications-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- AllowActionCenterNotifications-Editable-End -->

<!-- AllowActionCenterNotifications-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 1 |
<!-- AllowActionCenterNotifications-DFProperties-End -->

<!-- AllowActionCenterNotifications-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 | Not allowed. |
| 1 (Default) | Allowed. |
<!-- AllowActionCenterNotifications-AllowedValues-End -->

<!-- AllowActionCenterNotifications-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- AllowActionCenterNotifications-Examples-End -->

<!-- AllowActionCenterNotifications-End -->

<!-- AllowCortanaAboveLock-Begin -->
## AllowCortanaAboveLock

<!-- AllowCortanaAboveLock-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1607 [10.0.14393] and later |
<!-- AllowCortanaAboveLock-Applicability-End -->

<!-- AllowCortanaAboveLock-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/AboveLock/AllowCortanaAboveLock
```
<!-- AllowCortanaAboveLock-OmaUri-End -->

<!-- AllowCortanaAboveLock-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy setting determines whether or not the user can interact with Cortana using speech while the system is locked.

- If you enable or don't configure this setting, the user can interact with Cortana using speech while the system is locked.

- If you disable this setting, the system will need to be unlocked for the user to interact with Cortana using speech.
<!-- AllowCortanaAboveLock-Description-End -->

<!-- AllowCortanaAboveLock-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- AllowCortanaAboveLock-Editable-End -->

<!-- AllowCortanaAboveLock-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 1 |
<!-- AllowCortanaAboveLock-DFProperties-End -->

<!-- AllowCortanaAboveLock-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 | Not allowed. |
| 1 (Default) | Allowed. |
<!-- AllowCortanaAboveLock-AllowedValues-End -->

<!-- AllowCortanaAboveLock-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | AllowCortanaAboveLock |
| Friendly Name | Allow Cortana above lock screen |
| Location | Computer Configuration |
| Path | Windows Components > Search |
| Registry Key Name | SOFTWARE\Policies\Microsoft\Windows\Windows Search |
| Registry Value Name | AllowCortanaAboveLock |
| ADMX File Name | Search.admx |
<!-- AllowCortanaAboveLock-GpMapping-End -->

<!-- AllowCortanaAboveLock-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- AllowCortanaAboveLock-Examples-End -->

<!-- AllowCortanaAboveLock-End -->

<!-- AllowToasts-Begin -->
## AllowToasts

<!-- AllowToasts-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1607 [10.0.14393] and later |
<!-- AllowToasts-Applicability-End -->

<!-- AllowToasts-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/AboveLock/AllowToasts
```
<!-- AllowToasts-OmaUri-End -->

<!-- AllowToasts-Description-Begin -->
<!-- Description-Source-DDF -->
Specifies whether to allow toast notifications above the device lock screen. Most restricted value is 0.
<!-- AllowToasts-Description-End -->

<!-- AllowToasts-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- AllowToasts-Editable-End -->

<!-- AllowToasts-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 1 |
<!-- AllowToasts-DFProperties-End -->

<!-- AllowToasts-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 | Not allowed. |
| 1 (Default) | Allowed. |
<!-- AllowToasts-AllowedValues-End -->

<!-- AllowToasts-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- AllowToasts-Examples-End -->

<!-- AllowToasts-End -->

<!-- ConfigureAudioOnLockScreen-Begin -->
## ConfigureAudioOnLockScreen

<!-- ConfigureAudioOnLockScreen-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- ConfigureAudioOnLockScreen-Applicability-End -->

<!-- ConfigureAudioOnLockScreen-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/AboveLock/ConfigureAudioOnLockScreen
```
<!-- ConfigureAudioOnLockScreen-OmaUri-End -->

<!-- ConfigureAudioOnLockScreen-Description-Begin -->
<!-- Description-Source-DDF -->
This policy will allow the audio above lock screen to be managed by IT admins and allow apps like digital signage to play audio above lock screen without having a user signed on.
<!-- ConfigureAudioOnLockScreen-Description-End -->

<!-- ConfigureAudioOnLockScreen-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- ConfigureAudioOnLockScreen-Editable-End -->

<!-- ConfigureAudioOnLockScreen-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- ConfigureAudioOnLockScreen-DFProperties-End -->

<!-- ConfigureAudioOnLockScreen-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | No audio playback or recording on lock screen (aside from OS defined exceptions). |
| 1 | Audio playback allowed on lock screen. Audio recording isn't allowed. |
| 2 | Audio playback and recording allowed on lock screen. |
<!-- ConfigureAudioOnLockScreen-AllowedValues-End -->

<!-- ConfigureAudioOnLockScreen-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | ConfigureAudioOnLockScreen |
| Path | Audio > AT > WindowsComponents > Audio |
| Element Name | ConfigureAudioOnLockScreen_Enum |
<!-- ConfigureAudioOnLockScreen-GpMapping-End -->

<!-- ConfigureAudioOnLockScreen-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- ConfigureAudioOnLockScreen-Examples-End -->

<!-- ConfigureAudioOnLockScreen-End -->

<!-- AboveLock-CspMoreInfo-Begin -->
<!-- Add any additional information about this CSP here. Anything outside this section will get overwritten. -->
<!-- AboveLock-CspMoreInfo-End -->

<!-- AboveLock-End -->

## Related articles

[Policy configuration service provider](policy-configuration-service-provider.md)
