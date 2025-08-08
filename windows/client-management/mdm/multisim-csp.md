---
title: MultiSIM CSP
description: Learn more about the MultiSIM CSP.
ms.date: 06/10/2025
ms.topic: generated-reference
---

<!-- Auto-Generated CSP Document -->

<!-- MultiSIM-Begin -->
# MultiSIM CSP

<!-- MultiSIM-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
The MultiSIM configuration service provider (CSP) is used by the enterprise to manage devices with dual SIM single active configuration. An enterprise can set policies on whether that user can switch between SIM slots, specify which slot is the default, and whether the slot is embedded.
<!-- MultiSIM-Editable-End -->

<!-- MultiSIM-Tree-Begin -->
The following list shows the MultiSIM configuration service provider nodes:

- ./Device/Vendor/MSFT/MultiSIM
  - [{ModemID}](#modemid)
    - [Identifier](#modemididentifier)
    - [IsEmbedded](#modemidisembedded)
    - [Policies](#modemidpolicies)
      - [SlotSelectionEnabled](#modemidpoliciesslotselectionenabled)
    - [Slots](#modemidslots)
      - [{SlotID}](#modemidslotsslotid)
        - [Identifier](#modemidslotsslotididentifier)
        - [IsEmbedded](#modemidslotsslotidisembedded)
        - [IsSelected](#modemidslotsslotidisselected)
        - [State](#modemidslotsslotidstate)
<!-- MultiSIM-Tree-End -->

<!-- Device-{ModemID}-Begin -->
## {ModemID}

<!-- Device-{ModemID}-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1803 [10.0.17134] and later |
<!-- Device-{ModemID}-Applicability-End -->

<!-- Device-{ModemID}-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/MultiSIM/{ModemID}
```
<!-- Device-{ModemID}-OmaUri-End -->

<!-- Device-{ModemID}-Description-Begin -->
<!-- Description-Source-DDF -->
Node representing a Mobile Broadband Modem. The node name is the Modem ID. Modem ID is a GUID without curly braces, with exception of "Embedded" which represents the embedded Modem.
<!-- Device-{ModemID}-Description-End -->

<!-- Device-{ModemID}-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-{ModemID}-Editable-End -->

<!-- Device-{ModemID}-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Get |
| Dynamic Node Naming | UniqueName: The Modem ID associated with the device. |
<!-- Device-{ModemID}-DFProperties-End -->

<!-- Device-{ModemID}-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-{ModemID}-Examples-End -->

<!-- Device-{ModemID}-End -->

<!-- Device-{ModemID}-Identifier-Begin -->
### {ModemID}/Identifier

<!-- Device-{ModemID}-Identifier-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1803 [10.0.17134] and later |
<!-- Device-{ModemID}-Identifier-Applicability-End -->

<!-- Device-{ModemID}-Identifier-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/MultiSIM/{ModemID}/Identifier
```
<!-- Device-{ModemID}-Identifier-OmaUri-End -->

<!-- Device-{ModemID}-Identifier-Description-Begin -->
<!-- Description-Source-DDF -->
Modem ID.
<!-- Device-{ModemID}-Identifier-Description-End -->

<!-- Device-{ModemID}-Identifier-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-{ModemID}-Identifier-Editable-End -->

<!-- Device-{ModemID}-Identifier-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Get |
<!-- Device-{ModemID}-Identifier-DFProperties-End -->

<!-- Device-{ModemID}-Identifier-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-{ModemID}-Identifier-Examples-End -->

<!-- Device-{ModemID}-Identifier-End -->

<!-- Device-{ModemID}-IsEmbedded-Begin -->
### {ModemID}/IsEmbedded

<!-- Device-{ModemID}-IsEmbedded-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1803 [10.0.17134] and later |
<!-- Device-{ModemID}-IsEmbedded-Applicability-End -->

<!-- Device-{ModemID}-IsEmbedded-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/MultiSIM/{ModemID}/IsEmbedded
```
<!-- Device-{ModemID}-IsEmbedded-OmaUri-End -->

<!-- Device-{ModemID}-IsEmbedded-Description-Begin -->
<!-- Description-Source-DDF -->
Indicates whether this Modem is embedded or external.
<!-- Device-{ModemID}-IsEmbedded-Description-End -->

<!-- Device-{ModemID}-IsEmbedded-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-{ModemID}-IsEmbedded-Editable-End -->

<!-- Device-{ModemID}-IsEmbedded-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `bool` |
| Access Type | Get |
<!-- Device-{ModemID}-IsEmbedded-DFProperties-End -->

<!-- Device-{ModemID}-IsEmbedded-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-{ModemID}-IsEmbedded-Examples-End -->

<!-- Device-{ModemID}-IsEmbedded-End -->

<!-- Device-{ModemID}-Policies-Begin -->
### {ModemID}/Policies

<!-- Device-{ModemID}-Policies-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1803 [10.0.17134] and later |
<!-- Device-{ModemID}-Policies-Applicability-End -->

<!-- Device-{ModemID}-Policies-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/MultiSIM/{ModemID}/Policies
```
<!-- Device-{ModemID}-Policies-OmaUri-End -->

<!-- Device-{ModemID}-Policies-Description-Begin -->
<!-- Description-Source-DDF -->
Policies associated with the Modem.
<!-- Device-{ModemID}-Policies-Description-End -->

<!-- Device-{ModemID}-Policies-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-{ModemID}-Policies-Editable-End -->

<!-- Device-{ModemID}-Policies-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Get |
<!-- Device-{ModemID}-Policies-DFProperties-End -->

<!-- Device-{ModemID}-Policies-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-{ModemID}-Policies-Examples-End -->

<!-- Device-{ModemID}-Policies-End -->

<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-Begin -->
#### {ModemID}/Policies/SlotSelectionEnabled

<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1803 [10.0.17134] and later |
<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-Applicability-End -->

<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/MultiSIM/{ModemID}/Policies/SlotSelectionEnabled
```
<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-OmaUri-End -->

<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-Description-Begin -->
<!-- Description-Source-DDF -->
Determines whether the user is allowed to change slots in the Cellular settings UI. Default is true.
<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-Description-End -->

<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-Editable-End -->

<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `bool` |
| Access Type | Get, Replace |
| Default Value  | true |
<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-DFProperties-End -->

<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| false | Disabled. |
| true (Default) | Enabled. |
<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-AllowedValues-End -->

<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-Examples-End -->

<!-- Device-{ModemID}-Policies-SlotSelectionEnabled-End -->

<!-- Device-{ModemID}-Slots-Begin -->
### {ModemID}/Slots

<!-- Device-{ModemID}-Slots-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1803 [10.0.17134] and later |
<!-- Device-{ModemID}-Slots-Applicability-End -->

<!-- Device-{ModemID}-Slots-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/MultiSIM/{ModemID}/Slots
```
<!-- Device-{ModemID}-Slots-OmaUri-End -->

<!-- Device-{ModemID}-Slots-Description-Begin -->
<!-- Description-Source-DDF -->
Represents all SIM slots in the Modem.
<!-- Device-{ModemID}-Slots-Description-End -->

<!-- Device-{ModemID}-Slots-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-{ModemID}-Slots-Editable-End -->

<!-- Device-{ModemID}-Slots-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Get |
<!-- Device-{ModemID}-Slots-DFProperties-End -->

<!-- Device-{ModemID}-Slots-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-{ModemID}-Slots-Examples-End -->

<!-- Device-{ModemID}-Slots-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-Begin -->
#### {ModemID}/Slots/{SlotID}

<!-- Device-{ModemID}-Slots-{SlotID}-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1803 [10.0.17134] and later |
<!-- Device-{ModemID}-Slots-{SlotID}-Applicability-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/MultiSIM/{ModemID}/Slots/{SlotID}
```
<!-- Device-{ModemID}-Slots-{SlotID}-OmaUri-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-Description-Begin -->
<!-- Description-Source-DDF -->
Node representing a SIM Slot. The node name is the Slot ID. SIM Slot ID format is "0", "1", etc., with exception of "Embedded" which represents the embedded Slot.
<!-- Device-{ModemID}-Slots-{SlotID}-Description-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-{ModemID}-Slots-{SlotID}-Editable-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Get |
| Dynamic Node Naming | UniqueName: The SIM slot ID. |
<!-- Device-{ModemID}-Slots-{SlotID}-DFProperties-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-{ModemID}-Slots-{SlotID}-Examples-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-Begin -->
##### {ModemID}/Slots/{SlotID}/Identifier

<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1803 [10.0.17134] and later |
<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-Applicability-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/MultiSIM/{ModemID}/Slots/{SlotID}/Identifier
```
<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-OmaUri-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-Description-Begin -->
<!-- Description-Source-DDF -->
Slot ID.
<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-Description-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-Editable-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Get |
<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-DFProperties-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-Examples-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-Identifier-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-Begin -->
##### {ModemID}/Slots/{SlotID}/IsEmbedded

<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1803 [10.0.17134] and later |
<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-Applicability-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/MultiSIM/{ModemID}/Slots/{SlotID}/IsEmbedded
```
<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-OmaUri-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-Description-Begin -->
<!-- Description-Source-DDF -->
Indicates whether this Slot is embedded or a physical SIM slot.
<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-Description-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-Editable-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `bool` |
| Access Type | Get |
<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-DFProperties-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-Examples-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsEmbedded-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-Begin -->
##### {ModemID}/Slots/{SlotID}/IsSelected

<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1803 [10.0.17134] and later |
<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-Applicability-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/MultiSIM/{ModemID}/Slots/{SlotID}/IsSelected
```
<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-OmaUri-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-Description-Begin -->
<!-- Description-Source-DDF -->
Indicates whether this Slot is selected or not.
<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-Description-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-Editable-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `bool` |
| Access Type | Get, Replace |
<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-DFProperties-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| false | Not selected. |
| true | Selected. |
<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-AllowedValues-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-Examples-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-IsSelected-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-State-Begin -->
##### {ModemID}/Slots/{SlotID}/State

<!-- Device-{ModemID}-Slots-{SlotID}-State-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1803 [10.0.17134] and later |
<!-- Device-{ModemID}-Slots-{SlotID}-State-Applicability-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-State-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/MultiSIM/{ModemID}/Slots/{SlotID}/State
```
<!-- Device-{ModemID}-Slots-{SlotID}-State-OmaUri-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-State-Description-Begin -->
<!-- Description-Source-DDF -->
Slot state (Unknown = 0, OffEmpty = 1, Off = 2, Empty = 3, NotReady = 4, Active = 5, Error = 6, ActiveEsim = 7, ActiveEsimNoProfile = 8)
<!-- Device-{ModemID}-Slots-{SlotID}-State-Description-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-State-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-{ModemID}-Slots-{SlotID}-State-Editable-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-State-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Get |
<!-- Device-{ModemID}-Slots-{SlotID}-State-DFProperties-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-State-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-{ModemID}-Slots-{SlotID}-State-Examples-End -->

<!-- Device-{ModemID}-Slots-{SlotID}-State-End -->

<!-- MultiSIM-CspMoreInfo-Begin -->
<!-- Add any additional information about this CSP here. Anything outside this section will get overwritten. -->
## Examples

- Get modem:

    ```xml
    <SyncML xmlns="SYNCML:SYNCML1.2">
      <SyncBody>
        <Get>
          <CmdID>1</CmdID>
          <Item>
            <Target>
              <LocURI>
                ./Vendor/MSFT/MultiSIM
              </LocURI>
            </Target>
          </Item>
        </Get>
        <Final/>
      </SyncBody>
    </SyncML>
    ```

- Get slots:

    ```xml
    <SyncML xmlns="SYNCML:SYNCML1.2">
      <SyncBody>
        <Get>
          <CmdID>1</CmdID>
          <Item>
            <Target>
              <LocURI>
                ./Vendor/MSFT/MultiSIM/Embedded/Slots
              </LocURI>
            </Target>
          </Item>
        </Get>
        <Final/>
      </SyncBody>
    </SyncML>
    ```

- Get slot state:

    ```xml
    <SyncML xmlns="SYNCML:SYNCML1.2">
      <SyncBody>
        <Get>
          <CmdID>1</CmdID>
          <Item>
            <Target>
              <LocURI>
                ./Vendor/MSFT/MultiSIM/Embedded/Slots/Embedded/State
              </LocURI>
            </Target>
          </Item>
        </Get>
        <Final/>
      </SyncBody>
    </SyncML>
    ```

- Select slot:

    ```xml
    <SyncML xmlns="SYNCML:SYNCML1.2">
      <SyncBody>
        <Replace>
          <CmdID>1</CmdID>
          <Item>
            <Target>
              <LocURI>
                ./Vendor/MSFT/MultiSIM/Embedded/Slots/0/IsSelected
              </LocURI>
            </Target>
            <Meta>
              <Format xmlns="syncml:metinf">bool</Format>
              <Type>text/plain</Type>
            </Meta>
            <Data>true</Data>
          </Item>
        </Replace>
        <Final/>
      </SyncBody>
    </SyncML>
    ```
<!-- MultiSIM-CspMoreInfo-End -->

<!-- MultiSIM-End -->

## Related articles

[Configuration service provider reference](configuration-service-provider-reference.md)
