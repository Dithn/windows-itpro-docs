---
title: RemoteRemediation CSP
description: Learn more about the RemoteRemediation CSP.
ms.date: 03/26/2025
ms.topic: generated-reference
---

<!-- Auto-Generated CSP Document -->

<!-- RemoteRemediation-Begin -->
# RemoteRemediation CSP

[!INCLUDE [Windows Insider tip](includes/mdm-insider-csp-note.md)]

<!-- RemoteRemediation-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- RemoteRemediation-Editable-End -->

<!-- RemoteRemediation-Tree-Begin -->
The following list shows the RemoteRemediation configuration service provider nodes:

- ./Vendor/MSFT/RemoteRemediation
  - [CloudRemediationSettings](#cloudremediationsettings)
    - [AutoRemediationSettings](#cloudremediationsettingsautoremediationsettings)
      - [EnableAutoRemediation](#cloudremediationsettingsautoremediationsettingsenableautoremediation)
      - [SetRetryInterval](#cloudremediationsettingsautoremediationsettingssetretryinterval)
      - [SetTimeToReboot](#cloudremediationsettingsautoremediationsettingssettimetoreboot)
    - [EnableCloudRemediation](#cloudremediationsettingsenablecloudremediation)
    - [NetworkSettings](#cloudremediationsettingsnetworksettings)
      - [NetworkCredentials](#cloudremediationsettingsnetworksettingsnetworkcredentials)
        - [NetworkPassword](#cloudremediationsettingsnetworksettingsnetworkcredentialsnetworkpassword)
        - [NetworkPasswordEncryptionStore](#cloudremediationsettingsnetworksettingsnetworkcredentialsnetworkpasswordencryptionstore)
        - [NetworkPasswordEncryptionType](#cloudremediationsettingsnetworksettingsnetworkcredentialsnetworkpasswordencryptiontype)
        - [NetworkSSID](#cloudremediationsettingsnetworksettingsnetworkcredentialsnetworkssid)
<!-- RemoteRemediation-Tree-End -->

<!-- Device-CloudRemediationSettings-Begin -->
## CloudRemediationSettings

<!-- Device-CloudRemediationSettings-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-CloudRemediationSettings-Applicability-End -->

<!-- Device-CloudRemediationSettings-OmaUri-Begin -->
```Device
./Vendor/MSFT/RemoteRemediation/CloudRemediationSettings
```
<!-- Device-CloudRemediationSettings-OmaUri-End -->

<!-- Device-CloudRemediationSettings-Description-Begin -->
<!-- Description-Source-DDF -->
Interior node containing settings related to cloud remediation. Delete on this node will reset all cloud remediation settings to their default values.
<!-- Device-CloudRemediationSettings-Description-End -->

<!-- Device-CloudRemediationSettings-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-Editable-End -->

<!-- Device-CloudRemediationSettings-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Add, Delete, Get, Replace |
| Atomic Required | True |
<!-- Device-CloudRemediationSettings-DFProperties-End -->

<!-- Device-CloudRemediationSettings-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-Examples-End -->

<!-- Device-CloudRemediationSettings-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-Begin -->
### CloudRemediationSettings/AutoRemediationSettings

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-Applicability-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-OmaUri-Begin -->
```Device
./Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/AutoRemediationSettings
```
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-OmaUri-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-Description-Begin -->
<!-- Description-Source-DDF -->
Interior node containing settings related to auto remediation. Delete on this node will reset all auto remediation settings to their default values.
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-Description-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-Editable-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Add, Delete, Get, Replace |
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-DFProperties-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-Examples-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-Begin -->
#### CloudRemediationSettings/AutoRemediationSettings/EnableAutoRemediation

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-Applicability-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-OmaUri-Begin -->
```Device
./Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/AutoRemediationSettings/EnableAutoRemediation
```
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-OmaUri-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-Description-Begin -->
<!-- Description-Source-DDF -->
Enable or disable auto remediation.
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-Description-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-Editable-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `bool` |
| Access Type | Add, Delete, Get, Replace |
| Dependency [EnableCloudRemediation] | Dependency Type: `DependsOn` <br> Dependency URI: `Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/EnableCloudRemediation` <br> Dependency Allowed Value: `true` <br> Dependency Allowed Value Type: `ENUM` <br>  |
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-DFProperties-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| true | Auto remediation enabled. |
| false | Auto remediation disabled. |
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-AllowedValues-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-Examples-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-EnableAutoRemediation-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-Begin -->
#### CloudRemediationSettings/AutoRemediationSettings/SetRetryInterval

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-Applicability-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-OmaUri-Begin -->
```Device
./Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/AutoRemediationSettings/SetRetryInterval
```
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-OmaUri-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-Description-Begin -->
<!-- Description-Source-DDF -->
Get/set the retry interval (in minutes) during auto cloud remediation. The retry interval shouldn't be higher than the time to reboot. "SetRetryInterval" is dependent on "EnableAutoRemediation" and only takes effect if "EnableAutoRemediation" is set to true. Otherwise, an invalid argument error will be returned and no changes will be made.
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-Description-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-Editable-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Allowed Values | Range: `[1,4320]` |
| Dependency [EnableAutoRemediation] | Dependency Type: `DependsOn` <br> Dependency URI: `Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/AutoRemediationSettings/EnableAutoRemediation` <br> Dependency Allowed Value: `true` <br> Dependency Allowed Value Type: `ENUM` <br>  |
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-DFProperties-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-Examples-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetRetryInterval-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-Begin -->
#### CloudRemediationSettings/AutoRemediationSettings/SetTimeToReboot

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-Applicability-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-OmaUri-Begin -->
```Device
./Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/AutoRemediationSettings/SetTimeToReboot
```
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-OmaUri-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-Description-Begin -->
<!-- Description-Source-DDF -->
Get/set the time to reboot (in minutes) during auto cloud remediation. The maximum time to reboot possible is 72 hours. "SetTimeToReboot" is dependent on "EnableAutoRemediation" and only takes effect if "EnableAutoRemediation" is set to true. Otherwise an invalid argument error will be returned and no changes will be made.
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-Description-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-Editable-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Allowed Values | Range: `[1-4320]` |
| Dependency [EnableAutoRemediation] | Dependency Type: `DependsOn` <br> Dependency URI: `Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/AutoRemediationSettings/EnableAutoRemediation` <br> Dependency Allowed Value: `true` <br> Dependency Allowed Value Type: `ENUM` <br>  |
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-DFProperties-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-Examples-End -->

<!-- Device-CloudRemediationSettings-AutoRemediationSettings-SetTimeToReboot-End -->

<!-- Device-CloudRemediationSettings-EnableCloudRemediation-Begin -->
### CloudRemediationSettings/EnableCloudRemediation

<!-- Device-CloudRemediationSettings-EnableCloudRemediation-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-CloudRemediationSettings-EnableCloudRemediation-Applicability-End -->

<!-- Device-CloudRemediationSettings-EnableCloudRemediation-OmaUri-Begin -->
```Device
./Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/EnableCloudRemediation
```
<!-- Device-CloudRemediationSettings-EnableCloudRemediation-OmaUri-End -->

<!-- Device-CloudRemediationSettings-EnableCloudRemediation-Description-Begin -->
<!-- Description-Source-DDF -->
Enable or disable cloud remediation.
<!-- Device-CloudRemediationSettings-EnableCloudRemediation-Description-End -->

<!-- Device-CloudRemediationSettings-EnableCloudRemediation-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-EnableCloudRemediation-Editable-End -->

<!-- Device-CloudRemediationSettings-EnableCloudRemediation-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `bool` |
| Access Type | Add, Delete, Get, Replace |
<!-- Device-CloudRemediationSettings-EnableCloudRemediation-DFProperties-End -->

<!-- Device-CloudRemediationSettings-EnableCloudRemediation-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| true | Cloud remediation enabled. |
| false | Cloud remediation disabled. |
<!-- Device-CloudRemediationSettings-EnableCloudRemediation-AllowedValues-End -->

<!-- Device-CloudRemediationSettings-EnableCloudRemediation-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-EnableCloudRemediation-Examples-End -->

<!-- Device-CloudRemediationSettings-EnableCloudRemediation-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-Begin -->
### CloudRemediationSettings/NetworkSettings

<!-- Device-CloudRemediationSettings-NetworkSettings-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-CloudRemediationSettings-NetworkSettings-Applicability-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-OmaUri-Begin -->
```Device
./Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/NetworkSettings
```
<!-- Device-CloudRemediationSettings-NetworkSettings-OmaUri-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-Description-Begin -->
<!-- Description-Source-DDF -->
Interior node containing settings related to network.
<!-- Device-CloudRemediationSettings-NetworkSettings-Description-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-NetworkSettings-Editable-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Add, Delete, Get, Replace |
<!-- Device-CloudRemediationSettings-NetworkSettings-DFProperties-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-NetworkSettings-Examples-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-Begin -->
#### CloudRemediationSettings/NetworkSettings/NetworkCredentials

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-Applicability-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-OmaUri-Begin -->
```Device
./Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/NetworkSettings/NetworkCredentials
```
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-OmaUri-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-Description-Begin -->
<!-- Description-Source-DDF -->
Interior node containing settings related to network credentials.
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-Description-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-Editable-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Add, Delete, Get, Replace |
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-DFProperties-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-Examples-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-Begin -->
##### CloudRemediationSettings/NetworkSettings/NetworkCredentials/NetworkPassword

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-Applicability-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-OmaUri-Begin -->
```Device
./Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/NetworkSettings/NetworkCredentials/NetworkPassword
```
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-OmaUri-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-Description-Begin -->
<!-- Description-Source-DDF -->
Get/Set the password for the wifi network that cloud remediation will attempt to connect during cloud remediation.
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-Description-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-Editable-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
| Dependency [EnableCloudRemediation] | Dependency Type: `DependsOn` <br> Dependency URI: `Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/AutoRemediationSettings/EnableAutoRemediation` <br> Dependency Allowed Value: `true` <br> Dependency Allowed Value Type: `ENUM` <br>  |
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-DFProperties-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-Examples-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPassword-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-Begin -->
##### CloudRemediationSettings/NetworkSettings/NetworkCredentials/NetworkPasswordEncryptionStore

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-Applicability-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-OmaUri-Begin -->
```Device
./Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/NetworkSettings/NetworkCredentials/NetworkPasswordEncryptionStore
```
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-OmaUri-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-Description-Begin -->
<!-- Description-Source-DDF -->
The encryption store that's specified if we are using a custom certificate for password encryption.
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-Description-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-Editable-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
| Dependency [EnableCloudRemediation] | Dependency Type: `DependsOn` <br> Dependency URI: `Vendor/MSFT/RemoteRemediation/CloudRemediationSettings//AutoRemediationSettings/EnableAutoRemediation` <br> Dependency Allowed Value: `true` <br> Dependency Allowed Value Type: `ENUM` <br>  |
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-DFProperties-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-Examples-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionStore-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-Begin -->
##### CloudRemediationSettings/NetworkSettings/NetworkCredentials/NetworkPasswordEncryptionType

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-Applicability-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-OmaUri-Begin -->
```Device
./Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/NetworkSettings/NetworkCredentials/NetworkPasswordEncryptionType
```
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-OmaUri-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-Description-Begin -->
<!-- Description-Source-DDF -->
The type of encryption that might be used for the network password.
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-Description-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-Editable-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Dependency [EnableCloudRemediation] | Dependency Type: `DependsOn` <br> Dependency URI: `Vendor/MSFT/RemoteRemediation/CloudRemediationSettings//AutoRemediationSettings/EnableAutoRemediation` <br> Dependency Allowed Value: `true` <br> Dependency Allowed Value Type: `ENUM` <br>  |
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-DFProperties-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 1 | No encryption. |
| 2 | Encrypt using Mdm certificate. |
| 3 | Encrypt with custom certificate. |
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-AllowedValues-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-Examples-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkPasswordEncryptionType-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-Begin -->
##### CloudRemediationSettings/NetworkSettings/NetworkCredentials/NetworkSSID

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-Applicability-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-OmaUri-Begin -->
```Device
./Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/NetworkSettings/NetworkCredentials/NetworkSSID
```
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-OmaUri-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-Description-Begin -->
<!-- Description-Source-DDF -->
Get/Set the network SSID that cloud remediation will attempt to connect to during remediation.
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-Description-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-Editable-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
| Dependency [EnableCloudRemediation] | Dependency Type: `DependsOn` <br> Dependency URI: `Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/AutoRemediationSettings/EnableAutoRemediation` <br> Dependency Allowed Value: `true` <br> Dependency Allowed Value Type: `ENUM` <br>  |
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-DFProperties-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-Examples-End -->

<!-- Device-CloudRemediationSettings-NetworkSettings-NetworkCredentials-NetworkSSID-End -->

<!-- RemoteRemediation-CspMoreInfo-Begin -->
<!-- Add any additional information about this CSP here. Anything outside this section will get overwritten. -->
<!-- RemoteRemediation-CspMoreInfo-End -->

<!-- RemoteRemediation-End -->

## Related articles

[Configuration service provider reference](configuration-service-provider-reference.md)
