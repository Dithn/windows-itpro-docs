---
title: WindowsAI Policy CSP
description: Learn more about the WindowsAI Area in Policy CSP.
ms.date: 07/22/2025
ms.topic: generated-reference
---

<!-- Auto-Generated CSP Document -->

<!-- WindowsAI-Begin -->
# Policy CSP - WindowsAI

[!INCLUDE [Windows Insider tip](includes/mdm-insider-csp-note.md)]

<!-- WindowsAI-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- WindowsAI-Editable-End -->

<!-- AllowRecallEnablement-Begin -->
## AllowRecallEnablement

<!-- AllowRecallEnablement-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 with [KB5055627](https://support.microsoft.com/help/5055627) [10.0.26100.3915] and later |
<!-- AllowRecallEnablement-Applicability-End -->

<!-- AllowRecallEnablement-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/WindowsAI/AllowRecallEnablement
```
<!-- AllowRecallEnablement-OmaUri-End -->

<!-- AllowRecallEnablement-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy setting allows you to determine whether the Recall optional component is available for end users to enable on their device. By default, Recall is disabled for managed commercial devices. Recall isn't available on managed devices by default, and individual users can't enable Recall on their own.

- If this policy isn't configured, end users will have the Recall component in a disabled state.

- If this policy is disabled, the Recall component will be in disabled state and the bits for Recall will be removed from the device. If snapshots were previously saved on the device, they'll be deleted when this policy is disabled. Removing Recall requires a device restart.

- If the policy is enabled, end users will have Recall available on their device. Depending on the state of the DisableAIDataAnalysis policy (Turn off saving snapshots for use with Recall), end users will be able to choose if they want to save snapshots of their screen and use Recall to find things they've seen on their device.
<!-- AllowRecallEnablement-Description-End -->

<!-- AllowRecallEnablement-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- AllowRecallEnablement-Editable-End -->

<!-- AllowRecallEnablement-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 1 |
<!-- AllowRecallEnablement-DFProperties-End -->

<!-- AllowRecallEnablement-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 | Recall isn't available. |
| 1 (Default) | Recall is available. |
<!-- AllowRecallEnablement-AllowedValues-End -->

<!-- AllowRecallEnablement-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | AllowRecallEnablement |
| Friendly Name | Allow Recall to be enabled |
| Location | Computer Configuration |
| Path | Windows Components > Windows AI |
| Registry Key Name | SOFTWARE\Policies\Microsoft\Windows\WindowsAI |
| Registry Value Name | AllowRecallEnablement |
| ADMX File Name | WindowsCopilot.admx |
<!-- AllowRecallEnablement-GpMapping-End -->

<!-- AllowRecallEnablement-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- AllowRecallEnablement-Examples-End -->

<!-- AllowRecallEnablement-End -->

<!-- AllowRecallExport-Begin -->
## AllowRecallExport

<!-- AllowRecallExport-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- AllowRecallExport-Applicability-End -->

<!-- AllowRecallExport-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/WindowsAI/AllowRecallExport
```
<!-- AllowRecallExport-OmaUri-End -->

<!-- AllowRecallExport-Description-Begin -->
<!-- Description-Source-DDF -->
This policy allows you to determine whether users can export their own Recall and snapshot information. Exporting allows users to share their Recall and snapshot information with trusted apps or websites. Users can export from Settings > Privacy & security > Recall & snapshots > Advanced settings > Export snapshots > Export past snapshots > Export.

Users can also choose to continuously export their snapshots if they turn on the option to Export snapshots from now on from Settings > Privacy & security > Recall & snapshots > Advanced settings > Export snapshots > Export.

Before starting an export, the user must authenticate with Windows Hello and they're notified that their exported snapshots are encrypted since they might contain sensitive information. The user is also notified that they'll need to provide their Recall export code if they want to allow apps or websites access to exported snapshots. The Recall export code is displayed to users during Recall setup even if this policy is set to disabled or not configured. For managed devices:
- When you set this policy to enabled, users will be able to export Recall and snapshot information.
- If the policy is set to disabled or not configured, users won't be able to export their Recall and snapshot information.

> [!IMPORTANT]
> - This setting applies to devices in the European Economic Area (EEA) only. Export of Recall and snapshot information is a user-initiated process and is per user. IT admins or other users can't initiate an export on behalf of another.
> - Changes to this policy take effect after device restart.
<!-- AllowRecallExport-Description-End -->

<!-- AllowRecallExport-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- AllowRecallExport-Editable-End -->

<!-- AllowRecallExport-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- AllowRecallExport-DFProperties-End -->

<!-- AllowRecallExport-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Deny export of Recall and snapshots information. |
| 1 | Allow export of Recall and snapshot information. |
<!-- AllowRecallExport-AllowedValues-End -->

<!-- AllowRecallExport-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | AllowRecallExport |
| Path | WindowsAI > AT > WindowsComponents > WindowsAI |
<!-- AllowRecallExport-GpMapping-End -->

<!-- AllowRecallExport-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- AllowRecallExport-Examples-End -->

<!-- AllowRecallExport-End -->

<!-- DisableAIDataAnalysis-Begin -->
## DisableAIDataAnalysis

<!-- DisableAIDataAnalysis-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 with [KB5055627](https://support.microsoft.com/help/5055627) [10.0.26100.3915] and later |
<!-- DisableAIDataAnalysis-Applicability-End -->

<!-- DisableAIDataAnalysis-OmaUri-Begin -->
```User
./User/Vendor/MSFT/Policy/Config/WindowsAI/DisableAIDataAnalysis
```

```Device
./Device/Vendor/MSFT/Policy/Config/WindowsAI/DisableAIDataAnalysis
```
<!-- DisableAIDataAnalysis-OmaUri-End -->

<!-- DisableAIDataAnalysis-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy setting allows you to determine whether snapshots of the screen can be saved for use with Recall. By default, snapshots for Recall aren't enabled. IT administrators can't, on their own, enable saving snapshots on behalf of their users. The choice to enable saving snapshots requires individual user opt-in consent.

- If the policy isn't configured, snapshots won't be saved for use with Recall.

- If you enable this policy, snapshots won't be saved for use with Recall. If snapshots were previously saved on the device, they'll be deleted when this policy is enabled.

If you set this policy to disabled, end users will have a choice to save snapshots of their screen and use Recall to find things they've seen on their device.
<!-- DisableAIDataAnalysis-Description-End -->

<!-- DisableAIDataAnalysis-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- DisableAIDataAnalysis-Editable-End -->

<!-- DisableAIDataAnalysis-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- DisableAIDataAnalysis-DFProperties-End -->

<!-- DisableAIDataAnalysis-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Enable Saving Snapshots for Windows. |
| 1 | Disable Saving Snapshots for Windows. |
<!-- DisableAIDataAnalysis-AllowedValues-End -->

<!-- DisableAIDataAnalysis-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | DisableAIDataAnalysis |
| Friendly Name | Turn off saving snapshots for use with Recall |
| Location | Computer and User Configuration |
| Path | Windows Components > Windows AI |
| Registry Key Name | SOFTWARE\Policies\Microsoft\Windows\WindowsAI |
| Registry Value Name | DisableAIDataAnalysis |
| ADMX File Name | WindowsCopilot.admx |
<!-- DisableAIDataAnalysis-GpMapping-End -->

<!-- DisableAIDataAnalysis-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- DisableAIDataAnalysis-Examples-End -->

<!-- DisableAIDataAnalysis-End -->

<!-- DisableClickToDo-Begin -->
## DisableClickToDo

<!-- DisableClickToDo-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- DisableClickToDo-Applicability-End -->

<!-- DisableClickToDo-OmaUri-Begin -->
```User
./User/Vendor/MSFT/Policy/Config/WindowsAI/DisableClickToDo
```

```Device
./Device/Vendor/MSFT/Policy/Config/WindowsAI/DisableClickToDo
```
<!-- DisableClickToDo-OmaUri-End -->

<!-- DisableClickToDo-Description-Begin -->
<!-- Description-Source-DDF -->
Click to Do lets people take action on content on their screens. When activated, it takes a screenshot of their screen and analyzes it to present actions. Click to Do ends when they exit it, and it can't take screenshots while closed. Screenshot analysis is always performed locally on their device. By default, Click to Do is enabled for users. This policy setting allows you to determine whether Click to Do is available for users on their device. When the policy is enabled, the Click to Do component and entry points won't be available to users. When the policy is disabled, users will have Click to Do available on their device.
<!-- DisableClickToDo-Description-End -->

<!-- DisableClickToDo-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- DisableClickToDo-Editable-End -->

<!-- DisableClickToDo-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- DisableClickToDo-DFProperties-End -->

<!-- DisableClickToDo-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Click to Do is enabled. |
| 1 | Click to Do is disabled. |
<!-- DisableClickToDo-AllowedValues-End -->

<!-- DisableClickToDo-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | DisableClickToDo |
| Path | WindowsAI > AT > WindowsComponents > WindowsAI |
<!-- DisableClickToDo-GpMapping-End -->

<!-- DisableClickToDo-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- DisableClickToDo-Examples-End -->

<!-- DisableClickToDo-End -->

<!-- DisableCocreator-Begin -->
## DisableCocreator

<!-- DisableCocreator-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 22H2 [10.0.22621.4870] and later <br> ✅ Windows 11, version 24H2 [10.0.26100.3360] and later |
<!-- DisableCocreator-Applicability-End -->

<!-- DisableCocreator-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/WindowsAI/DisableCocreator
```
<!-- DisableCocreator-OmaUri-End -->

<!-- DisableCocreator-Description-Begin -->
<!-- Description-Source-DDF -->
This policy setting allows you to control whether Cocreator functionality is disabled in the Windows Paint app.

- If this policy is enabled, Cocreator functionality won't be accessible in the Paint app.

- If this policy is disabled or not configured, users will be able to access Cocreator functionality.
<!-- DisableCocreator-Description-End -->

<!-- DisableCocreator-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- DisableCocreator-Editable-End -->

<!-- DisableCocreator-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- DisableCocreator-DFProperties-End -->

<!-- DisableCocreator-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Cocreator is enabled. |
| 1 | Cocreator is disabled. |
<!-- DisableCocreator-AllowedValues-End -->

<!-- DisableCocreator-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | DisableCocreator |
| Path | WindowsAI > AT > WindowsComponents > Paint |
<!-- DisableCocreator-GpMapping-End -->

<!-- DisableCocreator-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- DisableCocreator-Examples-End -->

<!-- DisableCocreator-End -->

<!-- DisableGenerativeFill-Begin -->
## DisableGenerativeFill

<!-- DisableGenerativeFill-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 22H2 [10.0.22621.4870] and later <br> ✅ Windows 11, version 24H2 [10.0.26100.3360] and later |
<!-- DisableGenerativeFill-Applicability-End -->

<!-- DisableGenerativeFill-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/WindowsAI/DisableGenerativeFill
```
<!-- DisableGenerativeFill-OmaUri-End -->

<!-- DisableGenerativeFill-Description-Begin -->
<!-- Description-Source-DDF -->
This policy setting allows you to control whether generative fill functionality is disabled in the Windows Paint app.

- If this policy is enabled, generative fill functionality won't be accessible in the Paint app.

- If this policy is disabled or not configured, users will be able to access generative fill functionality.
<!-- DisableGenerativeFill-Description-End -->

<!-- DisableGenerativeFill-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- DisableGenerativeFill-Editable-End -->

<!-- DisableGenerativeFill-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- DisableGenerativeFill-DFProperties-End -->

<!-- DisableGenerativeFill-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Generative fill is enabled. |
| 1 | Generative fill is disabled. |
<!-- DisableGenerativeFill-AllowedValues-End -->

<!-- DisableGenerativeFill-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | DisableGenerativeFill |
| Path | WindowsAI > AT > WindowsComponents > Paint |
<!-- DisableGenerativeFill-GpMapping-End -->

<!-- DisableGenerativeFill-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- DisableGenerativeFill-Examples-End -->

<!-- DisableGenerativeFill-End -->

<!-- DisableImageCreator-Begin -->
## DisableImageCreator

<!-- DisableImageCreator-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 22H2 [10.0.22621.4870] and later <br> ✅ Windows 11, version 24H2 [10.0.26100.3360] and later |
<!-- DisableImageCreator-Applicability-End -->

<!-- DisableImageCreator-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/WindowsAI/DisableImageCreator
```
<!-- DisableImageCreator-OmaUri-End -->

<!-- DisableImageCreator-Description-Begin -->
<!-- Description-Source-DDF -->
This policy setting allows you to control whether Image Creator functionality is disabled in the Windows Paint app.

- If this policy is enabled, Image Creator functionality won't be accessible in the Paint app.

- If this policy is disabled or not configured, users will be able to access Image Creator functionality.
<!-- DisableImageCreator-Description-End -->

<!-- DisableImageCreator-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- DisableImageCreator-Editable-End -->

<!-- DisableImageCreator-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- DisableImageCreator-DFProperties-End -->

<!-- DisableImageCreator-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Image Creator is enabled. |
| 1 | Image Creator is disabled. |
<!-- DisableImageCreator-AllowedValues-End -->

<!-- DisableImageCreator-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | DisableImageCreator |
| Path | WindowsAI > AT > WindowsComponents > Paint |
<!-- DisableImageCreator-GpMapping-End -->

<!-- DisableImageCreator-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- DisableImageCreator-Examples-End -->

<!-- DisableImageCreator-End -->

<!-- DisableSettingsAgent-Begin -->
## DisableSettingsAgent

<!-- DisableSettingsAgent-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ❌ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- DisableSettingsAgent-Applicability-End -->

<!-- DisableSettingsAgent-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/WindowsAI/DisableSettingsAgent
```
<!-- DisableSettingsAgent-OmaUri-End -->

<!-- DisableSettingsAgent-Description-Begin -->
<!-- Description-Source-DDF -->
This policy setting allows you to determine whether Settings Agentic search experience is available for users on their device. When the policy is enabled, the agentic experience won't be available, limiting search results to statically indexed searches and semantic searches. When the policy is disabled, users will have Settings Agent search experience available on their device.
<!-- DisableSettingsAgent-Description-End -->

<!-- DisableSettingsAgent-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- DisableSettingsAgent-Editable-End -->

<!-- DisableSettingsAgent-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- DisableSettingsAgent-DFProperties-End -->

<!-- DisableSettingsAgent-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Settings Agentic search experience is enabled. |
| 1 | Settings Agentic search experience isn't enabled. |
<!-- DisableSettingsAgent-AllowedValues-End -->

<!-- DisableSettingsAgent-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | DisableSettingsAgent |
| Path | WindowsAI > AT > WindowsComponents > WindowsAI |
<!-- DisableSettingsAgent-GpMapping-End -->

<!-- DisableSettingsAgent-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- DisableSettingsAgent-Examples-End -->

<!-- DisableSettingsAgent-End -->

<!-- SetCopilotHardwareKey-Begin -->
## SetCopilotHardwareKey

<!-- SetCopilotHardwareKey-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ❌ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 22H2 with [KB5044380](https://support.microsoft.com/help/5044380) [10.0.22621.4391] and later |
<!-- SetCopilotHardwareKey-Applicability-End -->

<!-- SetCopilotHardwareKey-OmaUri-Begin -->
```User
./User/Vendor/MSFT/Policy/Config/WindowsAI/SetCopilotHardwareKey
```
<!-- SetCopilotHardwareKey-OmaUri-End -->

<!-- SetCopilotHardwareKey-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy setting determines which app opens when the user presses the Copilot key on their keyboard.

- If the policy is enabled, the specified app will open when the user presses the Copilot key. Users can change the key assignment in Settings.

- If the policy isn't configured, Copilot will open if it's available in that country or region.
<!-- SetCopilotHardwareKey-Description-End -->

<!-- SetCopilotHardwareKey-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
The property value is the Application User Model ID (AUMID) for the target application. For example: the Microsoft 365 Copilot app is `Microsoft.MicrosoftOfficeHub_8wekyb3d8bbwe!Microsoft.MicrosoftOfficeHub`. For more information, see [Find the application user model ID of an installed app](/windows/configuration/store/find-aumid?tabs=ps%2Cexplorer&pivots=windows-11).
<!-- SetCopilotHardwareKey-Editable-End -->

<!-- SetCopilotHardwareKey-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
<!-- SetCopilotHardwareKey-DFProperties-End -->

<!-- SetCopilotHardwareKey-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | SetCopilotHardwareKey |
| Friendly Name | Set Copilot Hardware Key |
| Location | User Configuration |
| Path | Windows Components > Windows Copilot |
| Registry Key Name | SOFTWARE\Policies\Microsoft\Windows\CopilotKey |
| ADMX File Name | WindowsCopilot.admx |
<!-- SetCopilotHardwareKey-GpMapping-End -->

<!-- SetCopilotHardwareKey-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- SetCopilotHardwareKey-Examples-End -->

<!-- SetCopilotHardwareKey-End -->

<!-- SetDenyAppListForRecall-Begin -->
## SetDenyAppListForRecall

<!-- SetDenyAppListForRecall-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ❌ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 with [KB5055627](https://support.microsoft.com/help/5055627) [10.0.26100.3915] and later |
<!-- SetDenyAppListForRecall-Applicability-End -->

<!-- SetDenyAppListForRecall-OmaUri-Begin -->
```User
./User/Vendor/MSFT/Policy/Config/WindowsAI/SetDenyAppListForRecall
```

```Device
./Device/Vendor/MSFT/Policy/Config/WindowsAI/SetDenyAppListForRecall
```
<!-- SetDenyAppListForRecall-OmaUri-End -->

<!-- SetDenyAppListForRecall-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy allows you to define a list of apps that won't be included in snapshots for Recall.

Users will be able to add additional applications to exclude from snapshots using Recall settings.

The list can include Application User Model IDs (AUMID) or name of the executable file.

Use a semicolon-separated list of apps to define the deny app list for Recall.

For example: `code.exe;Microsoft.WindowsNotepad_8wekyb3d8bbwe!App;ms-teams.exe`

> [!IMPORTANT]
> When configuring this policy setting, changes won't take effect until the device restarts.
<!-- SetDenyAppListForRecall-Description-End -->

<!-- SetDenyAppListForRecall-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- SetDenyAppListForRecall-Editable-End -->

<!-- SetDenyAppListForRecall-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
| Allowed Values | List (Delimiter: `;`) |
<!-- SetDenyAppListForRecall-DFProperties-End -->

<!-- SetDenyAppListForRecall-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | SetDenyAppListForRecall |
| Friendly Name | Set a list of apps to be filtered from snapshots for Recall |
| Location | Computer and User Configuration |
| Path | Windows Components > Windows AI |
| Registry Key Name | SOFTWARE\Policies\Microsoft\Windows\WindowsAI |
| Registry Value Name | SetDenyAppListForRecall |
| ADMX File Name | WindowsCopilot.admx |
<!-- SetDenyAppListForRecall-GpMapping-End -->

<!-- SetDenyAppListForRecall-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- SetDenyAppListForRecall-Examples-End -->

<!-- SetDenyAppListForRecall-End -->

<!-- SetDenyUriListForRecall-Begin -->
## SetDenyUriListForRecall

<!-- SetDenyUriListForRecall-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ❌ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 with [KB5055627](https://support.microsoft.com/help/5055627) [10.0.26100.3915] and later |
<!-- SetDenyUriListForRecall-Applicability-End -->

<!-- SetDenyUriListForRecall-OmaUri-Begin -->
```User
./User/Vendor/MSFT/Policy/Config/WindowsAI/SetDenyUriListForRecall
```

```Device
./Device/Vendor/MSFT/Policy/Config/WindowsAI/SetDenyUriListForRecall
```
<!-- SetDenyUriListForRecall-OmaUri-End -->

<!-- SetDenyUriListForRecall-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy setting lets you define a list of URIs that won't be included in snapshots for Recall when a supported browser is used. People within your organization can use Recall settings to add more websites to the list. Define the list using a semicolon to separate URIs.

For example: `https://www.Contoso.com;https://www.WoodgroveBank.com;https://www.Adatum.com`

Adding `https://www.WoodgroveBank.com` to the list would also filter `https://Account.WoodgroveBank.com` and `https://www.WoodgroveBank.com/Account`.

> [!IMPORTANT]
> Changes to this policy take effect after device restart.
<!-- SetDenyUriListForRecall-Description-End -->

<!-- SetDenyUriListForRecall-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- SetDenyUriListForRecall-Editable-End -->

<!-- SetDenyUriListForRecall-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
| Allowed Values | List (Delimiter: `;`) |
<!-- SetDenyUriListForRecall-DFProperties-End -->

<!-- SetDenyUriListForRecall-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | SetDenyUriListForRecall |
| Friendly Name | Set a list of URIs to be filtered from snapshots for Recall |
| Location | Computer and User Configuration |
| Path | Windows Components > Windows AI |
| Registry Key Name | SOFTWARE\Policies\Microsoft\Windows\WindowsAI |
| Registry Value Name | SetDenyUriListForRecall |
| ADMX File Name | WindowsCopilot.admx |
<!-- SetDenyUriListForRecall-GpMapping-End -->

<!-- SetDenyUriListForRecall-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- SetDenyUriListForRecall-Examples-End -->

<!-- SetDenyUriListForRecall-End -->

<!-- SetMaximumStorageDurationForRecallSnapshots-Begin -->
## SetMaximumStorageDurationForRecallSnapshots

<!-- SetMaximumStorageDurationForRecallSnapshots-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ❌ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 with [KB5055627](https://support.microsoft.com/help/5055627) [10.0.26100.3915] and later |
<!-- SetMaximumStorageDurationForRecallSnapshots-Applicability-End -->

<!-- SetMaximumStorageDurationForRecallSnapshots-OmaUri-Begin -->
```User
./User/Vendor/MSFT/Policy/Config/WindowsAI/SetMaximumStorageDurationForRecallSnapshots
```

```Device
./Device/Vendor/MSFT/Policy/Config/WindowsAI/SetMaximumStorageDurationForRecallSnapshots
```
<!-- SetMaximumStorageDurationForRecallSnapshots-OmaUri-End -->

<!-- SetMaximumStorageDurationForRecallSnapshots-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy setting allows you to control the maximum amount of time (in days) that Windows saves snapshots for Recall.

When the policy is enabled, you can configure the maximum storage duration to be 30, 60, 90, or 180 days.

When this policy isn't configured, a time frame isn't set for deleting snapshots.

Snapshots aren't deleted until the maximum storage allocation for Recall is reached, and then the oldest snapshots are deleted first.
<!-- SetMaximumStorageDurationForRecallSnapshots-Description-End -->

<!-- SetMaximumStorageDurationForRecallSnapshots-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- SetMaximumStorageDurationForRecallSnapshots-Editable-End -->

<!-- SetMaximumStorageDurationForRecallSnapshots-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- SetMaximumStorageDurationForRecallSnapshots-DFProperties-End -->

<!-- SetMaximumStorageDurationForRecallSnapshots-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Let the OS define the maximum amount of time the snapshots will be saved. |
| 30 | 30 days. |
| 60 | 60 days. |
| 90 | 90 days. |
| 180 | 180 days. |
<!-- SetMaximumStorageDurationForRecallSnapshots-AllowedValues-End -->

<!-- SetMaximumStorageDurationForRecallSnapshots-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | SetMaximumStorageDurationForRecallSnapshots |
| Friendly Name | Set maximum duration for storing snapshots used by Recall |
| Location | Computer and User Configuration |
| Path | Windows Components > Windows AI |
| Registry Key Name | SOFTWARE\Policies\Microsoft\Windows\WindowsAI |
| Registry Value Name | SetMaximumStorageDurationForRecallSnapshots |
| ADMX File Name | WindowsCopilot.admx |
<!-- SetMaximumStorageDurationForRecallSnapshots-GpMapping-End -->

<!-- SetMaximumStorageDurationForRecallSnapshots-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- SetMaximumStorageDurationForRecallSnapshots-Examples-End -->

<!-- SetMaximumStorageDurationForRecallSnapshots-End -->

<!-- SetMaximumStorageSpaceForRecallSnapshots-Begin -->
## SetMaximumStorageSpaceForRecallSnapshots

<!-- SetMaximumStorageSpaceForRecallSnapshots-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ❌ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 with [KB5055627](https://support.microsoft.com/help/5055627) [10.0.26100.3915] and later |
<!-- SetMaximumStorageSpaceForRecallSnapshots-Applicability-End -->

<!-- SetMaximumStorageSpaceForRecallSnapshots-OmaUri-Begin -->
```User
./User/Vendor/MSFT/Policy/Config/WindowsAI/SetMaximumStorageSpaceForRecallSnapshots
```

```Device
./Device/Vendor/MSFT/Policy/Config/WindowsAI/SetMaximumStorageSpaceForRecallSnapshots
```
<!-- SetMaximumStorageSpaceForRecallSnapshots-OmaUri-End -->

<!-- SetMaximumStorageSpaceForRecallSnapshots-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy setting allows you to control the maximum amount of disk space that can be used by Windows to save snapshots for Recall.

You can set the maximum amount of disk space for snapshots to be 10, 25, 50, 75, 100, or 150 GB.

When this setting isn't configured, the OS configures the storage allocation for snapshots based on the device storage capacity.

25 GB is allocated when the device storage capacity is 256 GB. 75 GB is allocated when the device storage capacity is 512 GB. 150 GB is allocated when the device storage capacity is 1 TB or higher.
<!-- SetMaximumStorageSpaceForRecallSnapshots-Description-End -->

<!-- SetMaximumStorageSpaceForRecallSnapshots-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- SetMaximumStorageSpaceForRecallSnapshots-Editable-End -->

<!-- SetMaximumStorageSpaceForRecallSnapshots-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- SetMaximumStorageSpaceForRecallSnapshots-DFProperties-End -->

<!-- SetMaximumStorageSpaceForRecallSnapshots-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Let the OS define the maximum storage amount based on hard drive storage size. |
| 10240 | 10GB. |
| 25600 | 25GB. |
| 51200 | 50GB. |
| 76800 | 75GB. |
| 102400 | 100GB. |
| 153600 | 150GB. |
<!-- SetMaximumStorageSpaceForRecallSnapshots-AllowedValues-End -->

<!-- SetMaximumStorageSpaceForRecallSnapshots-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | SetMaximumStorageSpaceForRecallSnapshots |
| Friendly Name | Set maximum storage for snapshots used by Recall |
| Location | Computer and User Configuration |
| Path | Windows Components > Windows AI |
| Registry Key Name | SOFTWARE\Policies\Microsoft\Windows\WindowsAI |
| Registry Value Name | SetMaximumStorageSpaceForRecallSnapshots |
| ADMX File Name | WindowsCopilot.admx |
<!-- SetMaximumStorageSpaceForRecallSnapshots-GpMapping-End -->

<!-- SetMaximumStorageSpaceForRecallSnapshots-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- SetMaximumStorageSpaceForRecallSnapshots-Examples-End -->

<!-- SetMaximumStorageSpaceForRecallSnapshots-End -->

<!-- TurnOffWindowsCopilot-Begin -->
## TurnOffWindowsCopilot

> [!NOTE]
> This policy is deprecated and may be removed in a future release.

<!-- TurnOffWindowsCopilot-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ❌ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 21H2 [10.0.19044.3758] and later <br> ✅ Windows 10, version 22H2 with [KB5032278](https://support.microsoft.com/help/5032278) [10.0.19045.3758] and later <br> ✅ Windows 11, version 22H2 with [KB5030310](https://support.microsoft.com/help/5030310) [10.0.22621.2361] and later <br> ✅ Windows 11, version 23H2 [10.0.22631] and later |
<!-- TurnOffWindowsCopilot-Applicability-End -->

<!-- TurnOffWindowsCopilot-OmaUri-Begin -->
```User
./User/Vendor/MSFT/Policy/Config/WindowsAI/TurnOffWindowsCopilot
```
<!-- TurnOffWindowsCopilot-OmaUri-End -->

<!-- TurnOffWindowsCopilot-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy setting allows you to turn off Windows Copilot.

- If you enable this policy setting, users won't be able to use Copilot. The Copilot icon won't appear on the taskbar either.

- If you disable or don't configure this policy setting, users will be able to use Copilot when it's available to them.
<!-- TurnOffWindowsCopilot-Description-End -->

<!-- TurnOffWindowsCopilot-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
> [!NOTE]
> - The TurnOffWindowsCopilot policy isn't for the [new Copilot experience](https://techcommunity.microsoft.com/blog/windows-itpro-blog/evolving-copilot-in-windows-for-your-workforce/4141999) that's in some [Windows Insider builds](https://blogs.windows.com/windows-insider/2024/05/22/releasing-windows-11-version-24h2-to-the-release-preview-channel/) and that will be gradually rolling out to Windows 11 and Windows 10 devices. <!--9048085-->
> - This policy also applies to upgrade scenarios to prevent installation of the Copilot app from an image that would have had the Copilot in Windows pane.
<!-- TurnOffWindowsCopilot-Editable-End -->

<!-- TurnOffWindowsCopilot-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- TurnOffWindowsCopilot-DFProperties-End -->

<!-- TurnOffWindowsCopilot-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Enable Copilot. |
| 1 | Disable Copilot. |
<!-- TurnOffWindowsCopilot-AllowedValues-End -->

<!-- TurnOffWindowsCopilot-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | TurnOffWindowsCopilot |
| Friendly Name | Turn off Windows Copilot |
| Location | User Configuration |
| Path | Windows Components > Windows Copilot |
| Registry Key Name | SOFTWARE\Policies\Microsoft\Windows\WindowsCopilot |
| Registry Value Name | TurnOffWindowsCopilot |
| ADMX File Name | WindowsCopilot.admx |
<!-- TurnOffWindowsCopilot-GpMapping-End -->

<!-- TurnOffWindowsCopilot-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- TurnOffWindowsCopilot-Examples-End -->

<!-- TurnOffWindowsCopilot-End -->

<!-- WindowsAI-CspMoreInfo-Begin -->
<!-- Add any additional information about this CSP here. Anything outside this section will get overwritten. -->
<!-- WindowsAI-CspMoreInfo-End -->

<!-- WindowsAI-End -->

## Related articles

[Policy configuration service provider](policy-configuration-service-provider.md)
