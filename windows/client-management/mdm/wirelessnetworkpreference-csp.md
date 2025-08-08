---
title: WirelessNetworkPreference CSP
description: Learn more about the WirelessNetworkPreference CSP.
ms.date: 06/09/2025
ms.topic: generated-reference
---

<!-- Auto-Generated CSP Document -->

<!-- WirelessNetworkPreference-Begin -->
# WirelessNetworkPreference CSP

[!INCLUDE [Windows Insider tip](includes/mdm-insider-csp-note.md)]

<!-- WirelessNetworkPreference-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- WirelessNetworkPreference-Editable-End -->

<!-- WirelessNetworkPreference-Tree-Begin -->
The following list shows the WirelessNetworkPreference configuration service provider nodes:

- ./Device/Vendor/MSFT/WirelessNetworkPreference
  - [ConnectionProfiles](#connectionprofiles)
    - [{ConnectionProfileID}](#connectionprofilesconnectionprofileid)
      - [Cellular](#connectionprofilesconnectionprofileidcellular)
        - [PLMNID](#connectionprofilesconnectionprofileidcellularplmnid)
      - [Priority](#connectionprofilesconnectionprofileidpriority)
      - [StayConnected](#connectionprofilesconnectionprofileidstayconnected)
      - [WirelessType](#connectionprofilesconnectionprofileidwirelesstype)
  - [IsEnabled](#isenabled)
  - [Parameters](#parameters)
    - [CellularParameters](#parameterscellularparameters)
      - [MaxRescanIntervalInSeconds](#parameterscellularparametersmaxrescanintervalinseconds)
      - [NetworkDiscoveryOption](#parameterscellularparametersnetworkdiscoveryoption)
      - [PreferredProfileWakeConnectionTimerInSeconds](#parameterscellularparameterspreferredprofilewakeconnectiontimerinseconds)
      - [ProfileRegistrationTimerInSeconds](#parameterscellularparametersprofileregistrationtimerinseconds)
      - [ScreenOffDurationToTriggerNetworkDiscoveryInMinutes](#parameterscellularparametersscreenoffdurationtotriggernetworkdiscoveryinminutes)
  - [PreferCellularOverWiFi](#prefercellularoverwifi)
  - [Status](#status)
    - [eSIMpolicyStatus](#statusesimpolicystatus)
    - [eSIMprofilesCount](#statusesimprofilescount)
    - [eSIMprofilesMatched](#statusesimprofilesmatched)
<!-- WirelessNetworkPreference-Tree-End -->

<!-- Device-ConnectionProfiles-Begin -->
## ConnectionProfiles

<!-- Device-ConnectionProfiles-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-ConnectionProfiles-Applicability-End -->

<!-- Device-ConnectionProfiles-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/ConnectionProfiles
```
<!-- Device-ConnectionProfiles-OmaUri-End -->

<!-- Device-ConnectionProfiles-Description-Begin -->
<!-- Description-Source-DDF -->
Profiles to connect to wireless networks in a specified priority order.
<!-- Device-ConnectionProfiles-Description-End -->

<!-- Device-ConnectionProfiles-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-Editable-End -->

<!-- Device-ConnectionProfiles-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Get |
<!-- Device-ConnectionProfiles-DFProperties-End -->

<!-- Device-ConnectionProfiles-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-Examples-End -->

<!-- Device-ConnectionProfiles-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Begin -->
### ConnectionProfiles/{ConnectionProfileID}

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Applicability-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/ConnectionProfiles/{ConnectionProfileID}
```
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-OmaUri-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Description-Begin -->
<!-- Description-Source-DDF -->
Unique identifier of a network preference policy. Unique ID is auto-generated.
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Description-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Editable-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Add, Delete, Get |
| Dynamic Node Naming | ServerGeneratedUniqueIdentifier |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-DFProperties-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Examples-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-Begin -->
#### ConnectionProfiles/{ConnectionProfileID}/Cellular

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-Applicability-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/ConnectionProfiles/{ConnectionProfileID}/Cellular
```
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-OmaUri-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-Description-Begin -->
<!-- Description-Source-DDF -->
Identifiers for cellular networks.
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-Description-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-Editable-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Add, Delete, Get |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-DFProperties-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-Examples-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-Begin -->
##### ConnectionProfiles/{ConnectionProfileID}/Cellular/PLMNID

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-Applicability-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/ConnectionProfiles/{ConnectionProfileID}/Cellular/PLMNID
```
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-OmaUri-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-Description-Begin -->
<!-- Description-Source-DDF -->
5- or 6-digit string identifying a cellular network. It consists of the combination of Mobile Country Code (MCC) and Mobile Network Code (MNC).
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-Description-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-Editable-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
| Allowed Values | Regular Expression: `^[0-9]{5,6}$` |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-DFProperties-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-Examples-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Cellular-PLMNID-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-Begin -->
#### ConnectionProfiles/{ConnectionProfileID}/Priority

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-Applicability-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/ConnectionProfiles/{ConnectionProfileID}/Priority
```
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-OmaUri-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-Description-Begin -->
<!-- Description-Source-DDF -->
Priority of a policy compared to the others where 1 represents the highest priority. Thus, the smaller this value is, the higher preference this specific network will receive in establishing a data connection.
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-Description-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-Editable-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Allowed Values | Range: `[1-2147483647]` |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-DFProperties-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-Examples-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-Priority-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-Begin -->
#### ConnectionProfiles/{ConnectionProfileID}/StayConnected

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-Applicability-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/ConnectionProfiles/{ConnectionProfileID}/StayConnected
```
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-OmaUri-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-Description-Begin -->
<!-- Description-Source-DDF -->
When set to 0: Default network discovery behavior is applied. When set to 1: Once connected, the device will always stay connected to this network. This means the device won't attempt to discover or switch to other higher priority networks until it first loses connectivity to this network.
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-Description-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-Editable-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-DFProperties-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Default network discovery behavior. |
| 1 | Once connected to this network, try to stay connected. |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-AllowedValues-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-Examples-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-StayConnected-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-Begin -->
#### ConnectionProfiles/{ConnectionProfileID}/WirelessType

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-Applicability-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/ConnectionProfiles/{ConnectionProfileID}/WirelessType
```
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-OmaUri-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-Description-Begin -->
<!-- Description-Source-DDF -->
Type of wireless network (either Cellular or Wi-Fi). 0 represents Cellular, and 1 represents Wi-Fi. Currently only cellular is supported.
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-Description-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-Editable-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `bin` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-DFProperties-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Cellular. |
| 1 | Wi-Fi. |
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-AllowedValues-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-Examples-End -->

<!-- Device-ConnectionProfiles-{ConnectionProfileID}-WirelessType-End -->

<!-- Device-IsEnabled-Begin -->
## IsEnabled

<!-- Device-IsEnabled-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-IsEnabled-Applicability-End -->

<!-- Device-IsEnabled-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/IsEnabled
```
<!-- Device-IsEnabled-OmaUri-End -->

<!-- Device-IsEnabled-Description-Begin -->
<!-- Description-Source-DDF -->
It determines whether the wireless connectivity management policy is enabled or not.
<!-- Device-IsEnabled-Description-End -->

<!-- Device-IsEnabled-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-IsEnabled-Editable-End -->

<!-- Device-IsEnabled-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `bool` |
| Access Type | Get, Replace |
| Default Value  | False |
<!-- Device-IsEnabled-DFProperties-End -->

<!-- Device-IsEnabled-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| False (Default) | Disable the wireless management policy. |
| True | Enable the wireless management policy. |
<!-- Device-IsEnabled-AllowedValues-End -->

<!-- Device-IsEnabled-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-IsEnabled-Examples-End -->

<!-- Device-IsEnabled-End -->

<!-- Device-Parameters-Begin -->
## Parameters

<!-- Device-Parameters-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-Parameters-Applicability-End -->

<!-- Device-Parameters-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/Parameters
```
<!-- Device-Parameters-OmaUri-End -->

<!-- Device-Parameters-Description-Begin -->
<!-- Description-Source-DDF -->
Parameters to configure the behavior of the wireless connectivity management service.
<!-- Device-Parameters-Description-End -->

<!-- Device-Parameters-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Parameters-Editable-End -->

<!-- Device-Parameters-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Get |
<!-- Device-Parameters-DFProperties-End -->

<!-- Device-Parameters-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Parameters-Examples-End -->

<!-- Device-Parameters-End -->

<!-- Device-Parameters-CellularParameters-Begin -->
### Parameters/CellularParameters

<!-- Device-Parameters-CellularParameters-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-Parameters-CellularParameters-Applicability-End -->

<!-- Device-Parameters-CellularParameters-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/Parameters/CellularParameters
```
<!-- Device-Parameters-CellularParameters-OmaUri-End -->

<!-- Device-Parameters-CellularParameters-Description-Begin -->
<!-- Description-Source-DDF -->
Parameters to configure the cellular-specific behavior of the wireless connectivity management service.
<!-- Device-Parameters-CellularParameters-Description-End -->

<!-- Device-Parameters-CellularParameters-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Parameters-CellularParameters-Editable-End -->

<!-- Device-Parameters-CellularParameters-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Get |
<!-- Device-Parameters-CellularParameters-DFProperties-End -->

<!-- Device-Parameters-CellularParameters-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Parameters-CellularParameters-Examples-End -->

<!-- Device-Parameters-CellularParameters-End -->

<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-Begin -->
#### Parameters/CellularParameters/MaxRescanIntervalInSeconds

<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-Applicability-End -->

<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/Parameters/CellularParameters/MaxRescanIntervalInSeconds
```
<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-OmaUri-End -->

<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-Description-Begin -->
<!-- Description-Source-DDF -->
Maximum time (in seconds) from the point that no connection could be established using the permissible eSIM profiles on the device to the start of the next round of network discovery attempts. A smaller interval increases network discovery frequency and can decrease battery life significantly. A value of 0 means that the device is to pick a reasonable interval per its own discretion.
<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-Description-End -->

<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-Editable-End -->

<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Get, Replace |
| Allowed Values | Range: `[0-360]` |
| Default Value  | 0 |
<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-DFProperties-End -->

<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-Examples-End -->

<!-- Device-Parameters-CellularParameters-MaxRescanIntervalInSeconds-End -->

<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-Begin -->
#### Parameters/CellularParameters/NetworkDiscoveryOption

<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-Applicability-End -->

<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/Parameters/CellularParameters/NetworkDiscoveryOption
```
<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-OmaUri-End -->

<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-Description-Begin -->
<!-- Description-Source-DDF -->
Configures which approach should be used in the network discovery process. There are two possible values: (0) no network scan will be performed - rather, registration and connection will be attempted with each eSIM profile in descending order of preference; or (1) Network scan will be performed using the current active eSIM profile. This option works for modems that when performing a network scan show the complete list of available networks independently of which eSIM profile is active.
<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-Description-End -->

<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-Editable-End -->

<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Get, Replace |
| Default Value  | 0 |
<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-DFProperties-End -->

<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | No network scan will be performed -- rather, registration and connection will be attempted with each eSIM profile in descending order of preference. |
| 1 | Network scan will be performed using the current active eSIM profile. |
<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-AllowedValues-End -->

<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-Examples-End -->

<!-- Device-Parameters-CellularParameters-NetworkDiscoveryOption-End -->

<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-Begin -->
#### Parameters/CellularParameters/PreferredProfileWakeConnectionTimerInSeconds

<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-Applicability-End -->

<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/Parameters/CellularParameters/PreferredProfileWakeConnectionTimerInSeconds
```
<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-OmaUri-End -->

<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-Description-Begin -->
<!-- Description-Source-DDF -->
When the device is woken from sleep with the most-preferred profile already enabled, this value configures the amount of time (in seconds) before the agent will give up on waiting for connection re-establishment with the most-preferred profile and start network discovery.
<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-Description-End -->

<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-Editable-End -->

<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Get, Replace |
| Allowed Values | Range: `[30-360]` |
| Default Value  | 200 |
<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-DFProperties-End -->

<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-Examples-End -->

<!-- Device-Parameters-CellularParameters-PreferredProfileWakeConnectionTimerInSeconds-End -->

<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-Begin -->
#### Parameters/CellularParameters/ProfileRegistrationTimerInSeconds

<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-Applicability-End -->

<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/Parameters/CellularParameters/ProfileRegistrationTimerInSeconds
```
<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-OmaUri-End -->

<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-Description-Begin -->
<!-- Description-Source-DDF -->
When evaluating eSIM profiles for connectivity, this value configures the amount of time (in seconds) that the agent will wait for network registration before considering this profile unsatisfactory and moving on to the next one.
<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-Description-End -->

<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-Editable-End -->

<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Get, Replace |
| Allowed Values | Range: `[20-360]` |
| Default Value  | 30 |
<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-DFProperties-End -->

<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-Examples-End -->

<!-- Device-Parameters-CellularParameters-ProfileRegistrationTimerInSeconds-End -->

<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-Begin -->
#### Parameters/CellularParameters/ScreenOffDurationToTriggerNetworkDiscoveryInMinutes

<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-Applicability-End -->

<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/Parameters/CellularParameters/ScreenOffDurationToTriggerNetworkDiscoveryInMinutes
```
<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-OmaUri-End -->

<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-Description-Begin -->
<!-- Description-Source-DDF -->
When the device experiences screen off and back on, this value configures the minimum duration (in minutes) of the screen off period that will trigger network discovery.
<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-Description-End -->

<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-Editable-End -->

<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Get, Replace |
| Allowed Values | Range: `[0-30]` |
| Default Value  | 10 |
<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-DFProperties-End -->

<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-Examples-End -->

<!-- Device-Parameters-CellularParameters-ScreenOffDurationToTriggerNetworkDiscoveryInMinutes-End -->

<!-- Device-PreferCellularOverWiFi-Begin -->
## PreferCellularOverWiFi

<!-- Device-PreferCellularOverWiFi-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-PreferCellularOverWiFi-Applicability-End -->

<!-- Device-PreferCellularOverWiFi-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/PreferCellularOverWiFi
```
<!-- Device-PreferCellularOverWiFi-OmaUri-End -->

<!-- Device-PreferCellularOverWiFi-Description-Begin -->
<!-- Description-Source-DDF -->
It determines the order of preference between Wi-Fi and cellular networks. When the value is set to "False", Wi-Fi is preferred over cellular. When the value is set to "True", cellular is preferred over Wi-Fi.
<!-- Device-PreferCellularOverWiFi-Description-End -->

<!-- Device-PreferCellularOverWiFi-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-PreferCellularOverWiFi-Editable-End -->

<!-- Device-PreferCellularOverWiFi-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `bool` |
| Access Type | Get, Replace |
| Default Value  | False |
<!-- Device-PreferCellularOverWiFi-DFProperties-End -->

<!-- Device-PreferCellularOverWiFi-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| False (Default) | Prefer Wi-Fi over Cellular. |
| True | Prefer Cellular over Wi-Fi. |
<!-- Device-PreferCellularOverWiFi-AllowedValues-End -->

<!-- Device-PreferCellularOverWiFi-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-PreferCellularOverWiFi-Examples-End -->

<!-- Device-PreferCellularOverWiFi-End -->

<!-- Device-Status-Begin -->
## Status

<!-- Device-Status-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-Status-Applicability-End -->

<!-- Device-Status-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/Status
```
<!-- Device-Status-OmaUri-End -->

<!-- Device-Status-Description-Begin -->
<!-- Description-Source-DDF -->
Nodes that indicate the status of the wireless connectivity management service.
<!-- Device-Status-Description-End -->

<!-- Device-Status-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Status-Editable-End -->

<!-- Device-Status-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Get |
<!-- Device-Status-DFProperties-End -->

<!-- Device-Status-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Status-Examples-End -->

<!-- Device-Status-End -->

<!-- Device-Status-eSIMpolicyStatus-Begin -->
### Status/eSIMpolicyStatus

<!-- Device-Status-eSIMpolicyStatus-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-Status-eSIMpolicyStatus-Applicability-End -->

<!-- Device-Status-eSIMpolicyStatus-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/Status/eSIMpolicyStatus
```
<!-- Device-Status-eSIMpolicyStatus-OmaUri-End -->

<!-- Device-Status-eSIMpolicyStatus-Description-Begin -->
<!-- Description-Source-DDF -->
An integer indicating the current status of the wireless connectivity management service. If the value is zero, there are no errors. \n\n 0 = No errors. \n 1 = No policies are configured. \n 2 = More than one policy has the same priority. \n 3 = More than one policy references the same PLMN ID. \n 4 = Invalid PLMN ID for one or more of the configured profiles. \n 5 = More than one eSIM profile stored in the eUICC with the same PLMN ID. \n 6 = Invalid configuration value for one or more of the cellular parameters. Please review CSP documentation. \n\n Warning: Any of these errors will result in a complete halt of the wireless connectivity management service.
<!-- Device-Status-eSIMpolicyStatus-Description-End -->

<!-- Device-Status-eSIMpolicyStatus-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Status-eSIMpolicyStatus-Editable-End -->

<!-- Device-Status-eSIMpolicyStatus-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Get |
<!-- Device-Status-eSIMpolicyStatus-DFProperties-End -->

<!-- Device-Status-eSIMpolicyStatus-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Status-eSIMpolicyStatus-Examples-End -->

<!-- Device-Status-eSIMpolicyStatus-End -->

<!-- Device-Status-eSIMprofilesCount-Begin -->
### Status/eSIMprofilesCount

<!-- Device-Status-eSIMprofilesCount-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-Status-eSIMprofilesCount-Applicability-End -->

<!-- Device-Status-eSIMprofilesCount-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/Status/eSIMprofilesCount
```
<!-- Device-Status-eSIMprofilesCount-OmaUri-End -->

<!-- Device-Status-eSIMprofilesCount-Description-Begin -->
<!-- Description-Source-DDF -->
Count of operational eSIM profiles stored in the eUICC.
<!-- Device-Status-eSIMprofilesCount-Description-End -->

<!-- Device-Status-eSIMprofilesCount-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Status-eSIMprofilesCount-Editable-End -->

<!-- Device-Status-eSIMprofilesCount-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Get |
<!-- Device-Status-eSIMprofilesCount-DFProperties-End -->

<!-- Device-Status-eSIMprofilesCount-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Status-eSIMprofilesCount-Examples-End -->

<!-- Device-Status-eSIMprofilesCount-End -->

<!-- Device-Status-eSIMprofilesMatched-Begin -->
### Status/eSIMprofilesMatched

<!-- Device-Status-eSIMprofilesMatched-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows Insider Preview |
<!-- Device-Status-eSIMprofilesMatched-Applicability-End -->

<!-- Device-Status-eSIMprofilesMatched-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WirelessNetworkPreference/Status/eSIMprofilesMatched
```
<!-- Device-Status-eSIMprofilesMatched-OmaUri-End -->

<!-- Device-Status-eSIMprofilesMatched-Description-Begin -->
<!-- Description-Source-DDF -->
Count of operational eSIM profiles stored on the eUICC whose PLMN ID matches one of the ConnectionProfileIDs setup under the ConnectionProfiles node. Only matched profiles with no errors will be counted. If more than one eSIM profile with the same PLMN ID is configured on the policy and/or more than one eSIM profile with the same PLMN ID is stored in the eUICC, then they won't be counted even if there is a match.
<!-- Device-Status-eSIMprofilesMatched-Description-End -->

<!-- Device-Status-eSIMprofilesMatched-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Status-eSIMprofilesMatched-Editable-End -->

<!-- Device-Status-eSIMprofilesMatched-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Get |
<!-- Device-Status-eSIMprofilesMatched-DFProperties-End -->

<!-- Device-Status-eSIMprofilesMatched-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Status-eSIMprofilesMatched-Examples-End -->

<!-- Device-Status-eSIMprofilesMatched-End -->

<!-- WirelessNetworkPreference-CspMoreInfo-Begin -->
<!-- Add any additional information about this CSP here. Anything outside this section will get overwritten. -->
<!-- WirelessNetworkPreference-CspMoreInfo-End -->

<!-- WirelessNetworkPreference-End -->

## Related articles

[Configuration service provider reference](configuration-service-provider-reference.md)
