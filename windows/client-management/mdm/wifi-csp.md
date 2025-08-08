---
title: WiFi CSP
description: Learn more about the WiFi CSP.
ms.date: 07/22/2025
ms.topic: generated-reference
---

<!-- Auto-Generated CSP Document -->

<!-- WiFi-Begin -->
# WiFi CSP

<!-- WiFi-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
The WiFi configuration service provider provides the functionality to add or delete Wi-Fi networks on a Windows device. The configuration service provider accepts SyncML input and converts it to a network profile that is installed on the device. This profile enables the device to connect to the Wi-Fi network when it's in range.

Programming considerations:

- If the authentication method needs a certificate (for example, client certificates for EAP-TLS), you must configure it through the [CertificateStore](certificatestore-csp.md) configuration service provider. The WiFi configuration service provider doesn't provide that functionality; instead, the Wi-Fi profile can specify characteristics of the certificate to be used for choosing the right certificate for that network. The server must successfully enroll the certificate first before deploying the Wi-Fi network configuration. For example, for an EAP-TLS profile, the server must successfully configure and enroll the required client certificate before deploying the Wi-Fi profile. Self-signed certificate works for EAP-TLS/PEAP-MSCHAPv2, but it isn't supported in EAP-TLS.
- For WEP, WPA, and WPA2-based networks, include the passkey in the network configuration in plaintext. The passkey is encrypted automatically when it's stored on the device.
- The `SSID` part of the LocURI node must be a valid URI based on RFC 2396. This condition requires that all nonexcluded ASCII characters must be escaped using a %-character, including replacing the space character (' ') with '%20'. Characters (including Unicode) without the necessary escaping aren't supported.
- For the WiFi CSP, you can't use the Replace command unless the node already exists.
- Using `Proxy`, `ProxyPacUrl` or `ProxyWPAD` in Windows client editions (Home, Pro, Enterprise, and Education) may fail or have no effect. Use [NetworkProxy](networkproxy-csp.md) CSP instead.
<!-- WiFi-Editable-End -->

<!-- WiFi-Tree-Begin -->
The following list shows the WiFi configuration service provider nodes:

- ./Device/Vendor/MSFT/WiFi
  - [Profile](#deviceprofile)
    - [{SSID}](#deviceprofilessid)
      - [ProfileSource](#deviceprofilessidprofilesource)
      - [Proxy](#deviceprofilessidproxy)
      - [ProxyPacUrl](#deviceprofilessidproxypacurl)
      - [ProxyWPAD](#deviceprofilessidproxywpad)
      - [WiFiCost](#deviceprofilessidwificost)
      - [WlanXml](#deviceprofilessidwlanxml)
- ./User/Vendor/MSFT/WiFi
  - [Profile](#userprofile)
    - [{SSID}](#userprofilessid)
      - [ProfileSource](#userprofilessidprofilesource)
      - [Proxy](#userprofilessidproxy)
      - [ProxyPacUrl](#userprofilessidproxypacurl)
      - [ProxyWPAD](#userprofilessidproxywpad)
      - [WiFiCost](#userprofilessidwificost)
      - [WlanXml](#userprofilessidwlanxml)
<!-- WiFi-Tree-End -->

<!-- Device-Profile-Begin -->
## Device/Profile

<!-- Device-Profile-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1511 [10.0.10586] and later |
<!-- Device-Profile-Applicability-End -->

<!-- Device-Profile-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WiFi/Profile
```
<!-- Device-Profile-OmaUri-End -->

<!-- Device-Profile-Description-Begin -->
<!-- Description-Source-DDF -->
Identifies the Wi-Fi network configuration. Each Wi-Fi network configuration is represented by a profile object. This network profile includes all the information required for the device to connect to that network - for example, the SSID, authentication and encryption methods and passphrase in case of WEP or WPA2 networks.
<!-- Device-Profile-Description-End -->

<!-- Device-Profile-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Profile-Editable-End -->

<!-- Device-Profile-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Get |
<!-- Device-Profile-DFProperties-End -->

<!-- Device-Profile-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Profile-Examples-End -->

<!-- Device-Profile-End -->

<!-- Device-Profile-{SSID}-Begin -->
### Device/Profile/{SSID}

<!-- Device-Profile-{SSID}-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1511 [10.0.10586] and later |
<!-- Device-Profile-{SSID}-Applicability-End -->

<!-- Device-Profile-{SSID}-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WiFi/Profile/{SSID}
```
<!-- Device-Profile-{SSID}-OmaUri-End -->

<!-- Device-Profile-{SSID}-Description-Begin -->
<!-- Description-Source-DDF -->
The Profile name of the Wi-Fi network. This is added when WlanXml node is added and deleted when WlanXml is deleted.
<!-- Device-Profile-{SSID}-Description-End -->

<!-- Device-Profile-{SSID}-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
Specifies the Profile name of the Wi-Fi network (32 bytes maximum) to create, configure, query, or delete. The name is case sensitive and can be represented in ASCII. In the URI, it must be %-escaped, but the non-%-escaped value is used inside the system.

> [!NOTE]
> This field is the Profile Name that appears as a "Friendly Name" to the user and contains the Wi-Fi settings information. The non-%-escaped value must correspond to `<name>` in `<WLANProfile> <name>`.

The Profile name can be the same or different from the SSID of the actual network being broadcast (which is under `<WLANProfile> <SSIDConfig> <SSID> <name>`). For example, the broadcast SSID might be "CC_Corp_7" but the Profile name might be "ContosoWiFi".
<!-- Device-Profile-{SSID}-Editable-End -->

<!-- Device-Profile-{SSID}-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Add, Delete, Get, Replace |
| Dynamic Node Naming | ServerGeneratedUniqueIdentifier |
<!-- Device-Profile-{SSID}-DFProperties-End -->

<!-- Device-Profile-{SSID}-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->

In the following example, the 'ContosoWiFi' Profile is added, targeting the 'CC_Corp_7' SSID. The rest of the profile is omitted for brevity - for complete examples, see [Add a network](#add-a-network).

```xml
<Atomic>
  <CmdID>300</CmdID>
  <Add>
    <CmdID>301</CmdID>
    <Item>
      <Target>
        <LocURI>./Vendor/MSFT/WiFi/Profile/ContosoWiFi/WlanXml</LocURI>
      </Target>
      <Meta>
        <Format xmlns="syncml:metinf">chr</Format>
      </Meta>
      <Data><![CDATA[<?xml version="1.0"?><WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1"><name>ContosoWiFi</name><SSIDConfig><SSID><name>CC_Corp_7</name></SSID></SSIDConfig>{...}</WLANProfile>]]></Data>
    </Item>
  </Add>
</Atomic>
```

> [!IMPORTANT]
> If the Profile name isn't set correctly in the MDM SyncML, as per the information in the Wi-Fi settings XML (`<WLANProfile>`), it could lead to some unexpected errors at runtime. In other words, if the profile is `<WLANProfile><name>Contoso Wi-Fi</name>{...}`, the MDM SyncML must be `<LocURI>./Vendor/MSFT/WiFi/Profile/Contoso%20Wi-Fi/WlanXml</LocURI>`.
>
> In this example, if we instead had `<LocURI>./Vendor/MSFT/WiFi/Profile/CC_Corp_7/WlanXml</LocURI>`, the profile would be considered to be User provisioned, not MDM provisioned, which may cause users to connect to the wrong network.
<!-- Device-Profile-{SSID}-Examples-End -->

<!-- Device-Profile-{SSID}-End -->

<!-- Device-Profile-{SSID}-ProfileSource-Begin -->
#### Device/Profile/{SSID}/ProfileSource

<!-- Device-Profile-{SSID}-ProfileSource-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 22H2 [10.0.22621] and later |
<!-- Device-Profile-{SSID}-ProfileSource-Applicability-End -->

<!-- Device-Profile-{SSID}-ProfileSource-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WiFi/Profile/{SSID}/ProfileSource
```
<!-- Device-Profile-{SSID}-ProfileSource-OmaUri-End -->

<!-- Device-Profile-{SSID}-ProfileSource-Description-Begin -->
<!-- Description-Source-DDF -->
Allows for defining which administrative entity is setting this Wi-Fi profile. This can currently be set to either 0=Enterprise or 1=Mobile Operator.
<!-- Device-Profile-{SSID}-ProfileSource-Description-End -->

<!-- Device-Profile-{SSID}-ProfileSource-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Profile-{SSID}-ProfileSource-Editable-End -->

<!-- Device-Profile-{SSID}-ProfileSource-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Get, Replace |
| Default Value  | 0 |
<!-- Device-Profile-{SSID}-ProfileSource-DFProperties-End -->

<!-- Device-Profile-{SSID}-ProfileSource-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Enterprise. |
| 1 | Mobile Operator. |
<!-- Device-Profile-{SSID}-ProfileSource-AllowedValues-End -->

<!-- Device-Profile-{SSID}-ProfileSource-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Profile-{SSID}-ProfileSource-Examples-End -->

<!-- Device-Profile-{SSID}-ProfileSource-End -->

<!-- Device-Profile-{SSID}-Proxy-Begin -->
#### Device/Profile/{SSID}/Proxy

<!-- Device-Profile-{SSID}-Proxy-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1511 [10.0.10586] and later |
<!-- Device-Profile-{SSID}-Proxy-Applicability-End -->

<!-- Device-Profile-{SSID}-Proxy-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WiFi/Profile/{SSID}/Proxy
```
<!-- Device-Profile-{SSID}-Proxy-OmaUri-End -->

<!-- Device-Profile-{SSID}-Proxy-Description-Begin -->
<!-- Description-Source-DDF -->
Optional node. The format is url:port. Configuration of the network proxy (if any).
<!-- Device-Profile-{SSID}-Proxy-Description-End -->

<!-- Device-Profile-{SSID}-Proxy-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
> [!NOTE]
> Don't use. Using this configuration in Windows client editions may fail or have no effect. Use [NetworkProxy](networkproxy-csp.md) CSP instead.
<!-- Device-Profile-{SSID}-Proxy-Editable-End -->

<!-- Device-Profile-{SSID}-Proxy-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
<!-- Device-Profile-{SSID}-Proxy-DFProperties-End -->

<!-- Device-Profile-{SSID}-Proxy-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Profile-{SSID}-Proxy-Examples-End -->

<!-- Device-Profile-{SSID}-Proxy-End -->

<!-- Device-Profile-{SSID}-ProxyPacUrl-Begin -->
#### Device/Profile/{SSID}/ProxyPacUrl

<!-- Device-Profile-{SSID}-ProxyPacUrl-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1607 [10.0.14393] and later |
<!-- Device-Profile-{SSID}-ProxyPacUrl-Applicability-End -->

<!-- Device-Profile-{SSID}-ProxyPacUrl-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WiFi/Profile/{SSID}/ProxyPacUrl
```
<!-- Device-Profile-{SSID}-ProxyPacUrl-OmaUri-End -->

<!-- Device-Profile-{SSID}-ProxyPacUrl-Description-Begin -->
<!-- Description-Source-DDF -->
Optional node. URL to the PAC file location.
<!-- Device-Profile-{SSID}-ProxyPacUrl-Description-End -->

<!-- Device-Profile-{SSID}-ProxyPacUrl-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
> [!NOTE]
> Don't use. Using this configuration in Windows client editions may fail or have no effect. Use [NetworkProxy](networkproxy-csp.md) CSP instead.
<!-- Device-Profile-{SSID}-ProxyPacUrl-Editable-End -->

<!-- Device-Profile-{SSID}-ProxyPacUrl-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
<!-- Device-Profile-{SSID}-ProxyPacUrl-DFProperties-End -->

<!-- Device-Profile-{SSID}-ProxyPacUrl-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Profile-{SSID}-ProxyPacUrl-Examples-End -->

<!-- Device-Profile-{SSID}-ProxyPacUrl-End -->

<!-- Device-Profile-{SSID}-ProxyWPAD-Begin -->
#### Device/Profile/{SSID}/ProxyWPAD

<!-- Device-Profile-{SSID}-ProxyWPAD-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1607 [10.0.14393] and later |
<!-- Device-Profile-{SSID}-ProxyWPAD-Applicability-End -->

<!-- Device-Profile-{SSID}-ProxyWPAD-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WiFi/Profile/{SSID}/ProxyWPAD
```
<!-- Device-Profile-{SSID}-ProxyWPAD-OmaUri-End -->

<!-- Device-Profile-{SSID}-ProxyWPAD-Description-Begin -->
<!-- Description-Source-DDF -->
Optional node. The presence of the field enables WPAD for proxy lookup.
<!-- Device-Profile-{SSID}-ProxyWPAD-Description-End -->

<!-- Device-Profile-{SSID}-ProxyWPAD-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
> [!NOTE]
> Don't use. Using this configuration in Windows client editions may fail or have no effect. Use [NetworkProxy](networkproxy-csp.md) CSP instead.
<!-- Device-Profile-{SSID}-ProxyWPAD-Editable-End -->

<!-- Device-Profile-{SSID}-ProxyWPAD-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `bool` |
| Access Type | Add, Delete, Get, Replace |
<!-- Device-Profile-{SSID}-ProxyWPAD-DFProperties-End -->

<!-- Device-Profile-{SSID}-ProxyWPAD-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| false | Disable WPAD for proxy lookup. |
| true | Enable WPAD for proxy lookup. |
<!-- Device-Profile-{SSID}-ProxyWPAD-AllowedValues-End -->

<!-- Device-Profile-{SSID}-ProxyWPAD-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Profile-{SSID}-ProxyWPAD-Examples-End -->

<!-- Device-Profile-{SSID}-ProxyWPAD-End -->

<!-- Device-Profile-{SSID}-WiFiCost-Begin -->
#### Device/Profile/{SSID}/WiFiCost

<!-- Device-Profile-{SSID}-WiFiCost-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1809 [10.0.17763] and later |
<!-- Device-Profile-{SSID}-WiFiCost-Applicability-End -->

<!-- Device-Profile-{SSID}-WiFiCost-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WiFi/Profile/{SSID}/WiFiCost
```
<!-- Device-Profile-{SSID}-WiFiCost-OmaUri-End -->

<!-- Device-Profile-{SSID}-WiFiCost-Description-Begin -->
<!-- Description-Source-DDF -->
Optional node. If the policy is active selecting one of the values from the following list will set the cost of WLAN connection for the Wi-Fi profile. (1:Unrestricted - unlimited connection, 2: Fixed - capacity constraints up to a certain data limit, 3: Variable - costed on per byte basic) Default behavior: Unrestricted.
<!-- Device-Profile-{SSID}-WiFiCost-Description-End -->

<!-- Device-Profile-{SSID}-WiFiCost-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- Device-Profile-{SSID}-WiFiCost-Editable-End -->

<!-- Device-Profile-{SSID}-WiFiCost-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 1 |
<!-- Device-Profile-{SSID}-WiFiCost-DFProperties-End -->

<!-- Device-Profile-{SSID}-WiFiCost-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 1 (Default) | Unrestricted - unlimited connection. |
| 2 | Fixed - capacity constraints up to a certain data limit. |
| 3 | Variable - paid on per byte basic. |
<!-- Device-Profile-{SSID}-WiFiCost-AllowedValues-End -->

<!-- Device-Profile-{SSID}-WiFiCost-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- Device-Profile-{SSID}-WiFiCost-Examples-End -->

<!-- Device-Profile-{SSID}-WiFiCost-End -->

<!-- Device-Profile-{SSID}-WlanXml-Begin -->
#### Device/Profile/{SSID}/WlanXml

<!-- Device-Profile-{SSID}-WlanXml-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1511 [10.0.10586] and later |
<!-- Device-Profile-{SSID}-WlanXml-Applicability-End -->

<!-- Device-Profile-{SSID}-WlanXml-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/WiFi/Profile/{SSID}/WlanXml
```
<!-- Device-Profile-{SSID}-WlanXml-OmaUri-End -->

<!-- Device-Profile-{SSID}-WlanXml-Description-Begin -->
<!-- Description-Source-DDF -->
XML describing the network configuration and follows Windows WLAN_profile schema.

Link to schema: <https://msdn.microsoft.com/library/windows/desktop/ms707341(v=vs.85).aspx>
<!-- Device-Profile-{SSID}-WlanXml-Description-End -->

<!-- Device-Profile-{SSID}-WlanXml-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
The profile XML must be escaped, as shown in the following examples.

If it exists in the blob, the **keyType** and **protected** elements must come before **keyMaterial**, as shown in the example in [WPA2-Personal Profile Sample](/windows/win32/nativewifi/wpa2-personal-profile-sample).

> [!NOTE]
> If you need to specify other advanced conditions, such as specifying criteria for certificates that can be used by the Wi-Fi profile, you can do so by specifying this through the [EapHostConfig](/windows/win32/eaphost/eaphostconfigschema-eaphostconfig-element) portion of the WlanXml ([WLANProfile](/windows/win32/nativewifi/wlan-profileschema-elements) > [MSM](/windows/win32/nativewifi/wlan-profileschema-msm-wlanprofile-element) > [security](/windows/win32/nativewifi/wlan-profileschema-security-msm-element) > [OneX](/windows/win32/nativewifi/onexschema-onex-element) > EAPConfig). For more information, see [EAP configuration](./eap-configuration.md) and [Extensible Authentication Protocol (EAP) for network access](/windows-server/networking/technologies/extensible-authentication-protocol/network-access). For an example, see [Wireless profile samples](/windows/win32/nativewifi/wireless-profile-samples).
<!-- Device-Profile-{SSID}-WlanXml-Editable-End -->

<!-- Device-Profile-{SSID}-WlanXml-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
<!-- Device-Profile-{SSID}-WlanXml-DFProperties-End -->

<!-- Device-Profile-{SSID}-WlanXml-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
See [Add a network](#add-a-network) for examples.
<!-- Device-Profile-{SSID}-WlanXml-Examples-End -->

<!-- Device-Profile-{SSID}-WlanXml-End -->

<!-- User-Profile-Begin -->
## User/Profile

<!-- User-Profile-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1511 [10.0.10586] and later |
<!-- User-Profile-Applicability-End -->

<!-- User-Profile-OmaUri-Begin -->
```User
./User/Vendor/MSFT/WiFi/Profile
```
<!-- User-Profile-OmaUri-End -->

<!-- User-Profile-Description-Begin -->
<!-- Description-Source-DDF -->
Identifies the Wi-Fi network configuration. Each Wi-Fi network configuration is represented by a profile object. This network profile includes all the information required for the device to connect to that network - for example, the SSID, authentication and encryption methods and passphrase in case of WEP or WPA2 networks.
<!-- User-Profile-Description-End -->

<!-- User-Profile-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- User-Profile-Editable-End -->

<!-- User-Profile-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Get |
<!-- User-Profile-DFProperties-End -->

<!-- User-Profile-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- User-Profile-Examples-End -->

<!-- User-Profile-End -->

<!-- User-Profile-{SSID}-Begin -->
### User/Profile/{SSID}

<!-- User-Profile-{SSID}-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1511 [10.0.10586] and later |
<!-- User-Profile-{SSID}-Applicability-End -->

<!-- User-Profile-{SSID}-OmaUri-Begin -->
```User
./User/Vendor/MSFT/WiFi/Profile/{SSID}
```
<!-- User-Profile-{SSID}-OmaUri-End -->

<!-- User-Profile-{SSID}-Description-Begin -->
<!-- Description-Source-DDF -->
The Profile name of the Wi-Fi network. This is added when WlanXml node is added and deleted when WlanXml is deleted.
<!-- User-Profile-{SSID}-Description-End -->

<!-- User-Profile-{SSID}-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
For more information, see [Device/Profile/{SSID}](#deviceprofilessid).
<!-- User-Profile-{SSID}-Editable-End -->

<!-- User-Profile-{SSID}-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `node` |
| Access Type | Add, Delete, Get, Replace |
| Dynamic Node Naming | ServerGeneratedUniqueIdentifier |
<!-- User-Profile-{SSID}-DFProperties-End -->

<!-- User-Profile-{SSID}-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- User-Profile-{SSID}-Examples-End -->

<!-- User-Profile-{SSID}-End -->

<!-- User-Profile-{SSID}-ProfileSource-Begin -->
#### User/Profile/{SSID}/ProfileSource

<!-- User-Profile-{SSID}-ProfileSource-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 22H2 [10.0.22621] and later |
<!-- User-Profile-{SSID}-ProfileSource-Applicability-End -->

<!-- User-Profile-{SSID}-ProfileSource-OmaUri-Begin -->
```User
./User/Vendor/MSFT/WiFi/Profile/{SSID}/ProfileSource
```
<!-- User-Profile-{SSID}-ProfileSource-OmaUri-End -->

<!-- User-Profile-{SSID}-ProfileSource-Description-Begin -->
<!-- Description-Source-DDF -->
Allows for defining which administrative entity is setting this Wi-Fi profile. This can currently be set to either 0=Enterprise or 1=Mobile Operator.
<!-- User-Profile-{SSID}-ProfileSource-Description-End -->

<!-- User-Profile-{SSID}-ProfileSource-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- User-Profile-{SSID}-ProfileSource-Editable-End -->

<!-- User-Profile-{SSID}-ProfileSource-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Get, Replace |
| Default Value  | 0 |
<!-- User-Profile-{SSID}-ProfileSource-DFProperties-End -->

<!-- User-Profile-{SSID}-ProfileSource-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Enterprise. |
| 1 | Mobile Operator. |
<!-- User-Profile-{SSID}-ProfileSource-AllowedValues-End -->

<!-- User-Profile-{SSID}-ProfileSource-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- User-Profile-{SSID}-ProfileSource-Examples-End -->

<!-- User-Profile-{SSID}-ProfileSource-End -->

<!-- User-Profile-{SSID}-Proxy-Begin -->
#### User/Profile/{SSID}/Proxy

<!-- User-Profile-{SSID}-Proxy-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1511 [10.0.10586] and later |
<!-- User-Profile-{SSID}-Proxy-Applicability-End -->

<!-- User-Profile-{SSID}-Proxy-OmaUri-Begin -->
```User
./User/Vendor/MSFT/WiFi/Profile/{SSID}/Proxy
```
<!-- User-Profile-{SSID}-Proxy-OmaUri-End -->

<!-- User-Profile-{SSID}-Proxy-Description-Begin -->
<!-- Description-Source-DDF -->
Optional node. The format is url:port. Configuration of the network proxy (if any).
<!-- User-Profile-{SSID}-Proxy-Description-End -->

<!-- User-Profile-{SSID}-Proxy-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
> [!NOTE]
> Don't use. Using this configuration in Windows client editions may fail or have no effect. Use [NetworkProxy](networkproxy-csp.md) CSP instead.
<!-- User-Profile-{SSID}-Proxy-Editable-End -->

<!-- User-Profile-{SSID}-Proxy-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
<!-- User-Profile-{SSID}-Proxy-DFProperties-End -->

<!-- User-Profile-{SSID}-Proxy-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- User-Profile-{SSID}-Proxy-Examples-End -->

<!-- User-Profile-{SSID}-Proxy-End -->

<!-- User-Profile-{SSID}-ProxyPacUrl-Begin -->
#### User/Profile/{SSID}/ProxyPacUrl

<!-- User-Profile-{SSID}-ProxyPacUrl-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1607 [10.0.14393] and later |
<!-- User-Profile-{SSID}-ProxyPacUrl-Applicability-End -->

<!-- User-Profile-{SSID}-ProxyPacUrl-OmaUri-Begin -->
```User
./User/Vendor/MSFT/WiFi/Profile/{SSID}/ProxyPacUrl
```
<!-- User-Profile-{SSID}-ProxyPacUrl-OmaUri-End -->

<!-- User-Profile-{SSID}-ProxyPacUrl-Description-Begin -->
<!-- Description-Source-DDF -->
Optional node. URL to the PAC file location.
<!-- User-Profile-{SSID}-ProxyPacUrl-Description-End -->

<!-- User-Profile-{SSID}-ProxyPacUrl-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
> [!NOTE]
> Don't use. Using this configuration in Windows client editions may fail or have no effect. Use [NetworkProxy](networkproxy-csp.md) CSP instead.
<!-- User-Profile-{SSID}-ProxyPacUrl-Editable-End -->

<!-- User-Profile-{SSID}-ProxyPacUrl-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
<!-- User-Profile-{SSID}-ProxyPacUrl-DFProperties-End -->

<!-- User-Profile-{SSID}-ProxyPacUrl-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- User-Profile-{SSID}-ProxyPacUrl-Examples-End -->

<!-- User-Profile-{SSID}-ProxyPacUrl-End -->

<!-- User-Profile-{SSID}-ProxyWPAD-Begin -->
#### User/Profile/{SSID}/ProxyWPAD

<!-- User-Profile-{SSID}-ProxyWPAD-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1607 [10.0.14393] and later |
<!-- User-Profile-{SSID}-ProxyWPAD-Applicability-End -->

<!-- User-Profile-{SSID}-ProxyWPAD-OmaUri-Begin -->
```User
./User/Vendor/MSFT/WiFi/Profile/{SSID}/ProxyWPAD
```
<!-- User-Profile-{SSID}-ProxyWPAD-OmaUri-End -->

<!-- User-Profile-{SSID}-ProxyWPAD-Description-Begin -->
<!-- Description-Source-DDF -->
Optional node. The presence of the field enables WPAD for proxy lookup.
<!-- User-Profile-{SSID}-ProxyWPAD-Description-End -->

<!-- User-Profile-{SSID}-ProxyWPAD-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
> [!NOTE]
> Don't use. Using this configuration in Windows client editions may fail or have no effect. Use [NetworkProxy](networkproxy-csp.md) CSP instead.
<!-- User-Profile-{SSID}-ProxyWPAD-Editable-End -->

<!-- User-Profile-{SSID}-ProxyWPAD-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `bool` |
| Access Type | Add, Delete, Get, Replace |
<!-- User-Profile-{SSID}-ProxyWPAD-DFProperties-End -->

<!-- User-Profile-{SSID}-ProxyWPAD-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| false | Disable WPAD for proxy lookup. |
| true | Enable WPAD for proxy lookup. |
<!-- User-Profile-{SSID}-ProxyWPAD-AllowedValues-End -->

<!-- User-Profile-{SSID}-ProxyWPAD-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- User-Profile-{SSID}-ProxyWPAD-Examples-End -->

<!-- User-Profile-{SSID}-ProxyWPAD-End -->

<!-- User-Profile-{SSID}-WiFiCost-Begin -->
#### User/Profile/{SSID}/WiFiCost

<!-- User-Profile-{SSID}-WiFiCost-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1809 [10.0.17763] and later |
<!-- User-Profile-{SSID}-WiFiCost-Applicability-End -->

<!-- User-Profile-{SSID}-WiFiCost-OmaUri-Begin -->
```User
./User/Vendor/MSFT/WiFi/Profile/{SSID}/WiFiCost
```
<!-- User-Profile-{SSID}-WiFiCost-OmaUri-End -->

<!-- User-Profile-{SSID}-WiFiCost-Description-Begin -->
<!-- Description-Source-DDF -->
Optional node. If the policy is active selecting one of the values from the following list will set the cost of WLAN connection for the Wi-Fi profile. (1:Unrestricted - unlimited connection, 2: Fixed - capacity constraints up to a certain data limit, 3: Variable - costed on per byte basic) Default behavior: Unrestricted.
<!-- User-Profile-{SSID}-WiFiCost-Description-End -->

<!-- User-Profile-{SSID}-WiFiCost-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- User-Profile-{SSID}-WiFiCost-Editable-End -->

<!-- User-Profile-{SSID}-WiFiCost-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 1 |
<!-- User-Profile-{SSID}-WiFiCost-DFProperties-End -->

<!-- User-Profile-{SSID}-WiFiCost-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 1 (Default) | Unrestricted - unlimited connection. |
| 2 | Fixed - capacity constraints up to a certain data limit. |
| 3 | Variable - paid on per byte basic. |
<!-- User-Profile-{SSID}-WiFiCost-AllowedValues-End -->

<!-- User-Profile-{SSID}-WiFiCost-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- User-Profile-{SSID}-WiFiCost-Examples-End -->

<!-- User-Profile-{SSID}-WiFiCost-End -->

<!-- User-Profile-{SSID}-WlanXml-Begin -->
#### User/Profile/{SSID}/WlanXml

<!-- User-Profile-{SSID}-WlanXml-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ✅ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1511 [10.0.10586] and later |
<!-- User-Profile-{SSID}-WlanXml-Applicability-End -->

<!-- User-Profile-{SSID}-WlanXml-OmaUri-Begin -->
```User
./User/Vendor/MSFT/WiFi/Profile/{SSID}/WlanXml
```
<!-- User-Profile-{SSID}-WlanXml-OmaUri-End -->

<!-- User-Profile-{SSID}-WlanXml-Description-Begin -->
<!-- Description-Source-DDF -->
XML describing the network configuration and follows Windows WLAN_profile schema.

Link to schema: <https://msdn.microsoft.com/library/windows/desktop/ms707341(v=vs.85).aspx>
<!-- User-Profile-{SSID}-WlanXml-Description-End -->

<!-- User-Profile-{SSID}-WlanXml-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->

For more information, see [Device/Profile/{SSID}/WlanXml](#deviceprofilessidwlanxml).
<!-- User-Profile-{SSID}-WlanXml-Editable-End -->

<!-- User-Profile-{SSID}-WlanXml-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `chr` (string) |
| Access Type | Add, Delete, Get, Replace |
<!-- User-Profile-{SSID}-WlanXml-DFProperties-End -->

<!-- User-Profile-{SSID}-WlanXml-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- User-Profile-{SSID}-WlanXml-Examples-End -->

<!-- User-Profile-{SSID}-WlanXml-End -->

<!-- WiFi-CspMoreInfo-Begin -->
<!-- Add any additional information about this CSP here. Anything outside this section will get overwritten. -->
## Examples

These XML examples show how to perform various tasks using OMA DM.

### Add a network

The following example shows how to add a WPA2-Enterprise network with SSID and profile name `MyNetwork` that authenticates with PEAP-MSCHAPv2. This example is based on the sample profile at [WPA2-Enterprise with PEAP-MSCHAPv2 profile sample](/windows/win32/nativewifi/wpa2-enterprise-with-peap-mschapv2-profile-sample).

```xml
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Atomic>
      <CmdID>301</CmdID>
      <Add>
        <CmdID>302</CmdID>
        <Item>
          <Target>
            <LocURI>./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml</LocURI>
          </Target>
          <Meta>
            <Format xmlns="syncml:metinf">chr</Format>
          </Meta>
          <Data><![CDATA[<?xml version="1.0"?><WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1"><name>MyNetwork</name><SSIDConfig><SSID><hex>4d794e6574776f726b</hex><name>MyNetwork</name></SSID><nonBroadcast>false</nonBroadcast></SSIDConfig><connectionType>ESS</connectionType><connectionMode>manual</connectionMode><MSM><security><authEncryption><authentication>WPA2</authentication><encryption>AES</encryption><useOneX>true</useOneX></authEncryption><OneX xmlns="http://www.microsoft.com/networking/OneX/v1"><authMode>user</authMode><EAPConfig><EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig"><EapMethod><Type xmlns="http://www.microsoft.com/provisioning/EapCommon">25</Type><VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId><VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType><AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId></EapMethod><Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig"><Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"><Type>25</Type><EapType xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV1"><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames></ServerNames></ServerValidation><FastReconnect>true</FastReconnect><InnerEapOptional>false</InnerEapOptional><Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"><Type>26</Type><EapType xmlns="http://www.microsoft.com/provisioning/MsChapV2ConnectionPropertiesV1"><UseWinLogonCredentials>false</UseWinLogonCredentials></EapType></Eap><EnableQuarantineChecks>false</EnableQuarantineChecks><RequireCryptoBinding>false</RequireCryptoBinding><PeapExtensions><PerformServerValidation xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">false</PerformServerValidation><AcceptServerName xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">false</AcceptServerName></PeapExtensions></EapType></Eap></Config></EapHostConfig></EAPConfig></OneX></security></MSM></WLANProfile>]]></Data>
        </Item>
      </Add>
    </Atomic>
    <Final/>
  </SyncBody>
</SyncML>
```

The following example shows how to add a WPA3-Enterprise network with profile name `My Network` and SSID `MySSID` that authenticates with EAP-TLS. This example is based on the sample profile at [WPA2-Enterprise with TLS profile sample](/windows/win32/nativewifi/wpa2-enterprise-with-tls-profile-sample).

> [!IMPORTANT]
> Notice how the space is %-escaped in the `LocURI` and unescaped in the `WLANProfile` > `name`.

```xml
<Atomic>
  <CmdID>300</CmdID>
  <Add>
    <CmdID>301</CmdID>
    <Item>
      <Target>
        <LocURI>./Vendor/MSFT/WiFi/Profile/My%20Network/WlanXml</LocURI>
      </Target>
      <Meta>
        <Format xmlns="syncml:metinf">chr</Format>
      </Meta>
      <Data><![CDATA[<?xml version="1.0"?><WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1"><name>My Network</name><SSIDConfig><SSID><name>MySSID</name></SSID></SSIDConfig><connectionType>ESS</connectionType><connectionMode>auto</connectionMode><MSM><security><authEncryption><authentication>WPA3ENT</authentication><encryption>AES</encryption><useOneX>true</useOneX></authEncryption><PMKCacheMode>enabled</PMKCacheMode><PMKCacheTTL>720</PMKCacheTTL><PMKCacheSize>128</PMKCacheSize><preAuthMode>disabled</preAuthMode><OneX xmlns="http://www.microsoft.com/networking/OneX/v1"><authMode>machine</authMode><EAPConfig><EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig"><EapMethod><Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type><VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId><VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType><AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId></EapMethod><Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig"><Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"><Type>13</Type><EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>00 11 22 33 44 55 66 77 88 99 aa bb cc dd ee ff 00 11 22 33</TrustedRootCA></ServerValidation><DifferentUsername>false</DifferentUsername><PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">true</PerformServerValidation><AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName><TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"><FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3"><AllPurposeEnabled>false</AllPurposeEnabled><CAHashList Enabled="true"><IssuerHash>00112233445566778899aabbccddeeff00112233</IssuerHash></CAHashList><EKUMapping><EKUMap><EKUName>Client Authentication</EKUName><EKUOID>1.3.6.1.5.5.7.3.2</EKUOID></EKUMap></EKUMapping><ClientAuthEKUList Enabled="true"><EKUMapInList><EKUName>Client Authentication</EKUName></EKUMapInList></ClientAuthEKUList></FilteringInfo></TLSExtensions></EapType></Eap></Config></EapHostConfig></EAPConfig></OneX></security></MSM></WLANProfile>]]></Data>
    </Item>
  </Add>
</Atomic>
```

The following example shows how to add a WPA3-Personal (transition mode) network with profile name and SSID `MyNetwork` that includes the passphrase `TestPassword1!`. This example is based on the sample profile at [WPA3-Personal with transition mode profile sample](/windows/win32/nativewifi/wpa3-personal-transition-profile-sample).

```xml
<Atomic>
  <CmdID>300</CmdID>
  <Add>
    <CmdID>301</CmdID>
    <Item>
      <Target>
        <LocURI>./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml</LocURI>
      </Target>
      <Meta>
        <Format xmlns="syncml:metinf">chr</Format>
      </Meta>
      <Data><![CDATA[<?xml version="1.0"?><WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1"><name>MyNetwork</name><SSIDConfig><SSID><name>MyNetwork</name></SSID></SSIDConfig><connectionType>ESS</connectionType><connectionMode>auto</connectionMode><MSM><security><authEncryption><authentication>WPA3SAE</authentication><encryption>AES</encryption><useOneX>false</useOneX><transitionMode xmlns="http://www.microsoft.com/networking/WLAN/profile/v4">true</transitionMode></authEncryption><sharedKey><keyType>passPhrase</keyType><protected>false</protected><keyMaterial>TestPassword1!</keyMaterial></sharedKey></security></MSM></WLANProfile>]]></Data>
    </Item>
  </Add>
</Atomic>
```

### Query network profiles

The following example shows how to query Wi-Fi profiles installed on an MDM server.

```xml
<Get>
   <CmdID>301</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/WiFi/Profile</LocURI>
      </Target>
   </Item>
</Get>
```

The following example shows the response.

```xml
<Results>
   <CmdID>3</CmdID>
   <MsgRef>1</MsgRef>
   <CmdRef>301</CmdRef>
   <Item>
      <Source><LocURI>./Vendor/MSFT/WiFi/Profile</LocURI></Source>
      <Meta><Format xmlns="syncml:metinf">node</Format></Meta>
      <Data>TestWLAN1/TestWLAN2</Data>
   </Item>
</Results>
```

### Remove a network

The following example shows how to remove a network with SSID `MyNetwork` and no proxy. Removing all network authentication types is done in this same manner.

```xml
<Atomic>
  <CmdID>300</CmdID>
  <Delete>
    <CmdID>301</CmdID>
    <Item>
      <Target>
        <LocURI>./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml</LocURI>
      </Target>
    </Item>
  </Delete>
</Atomic>
```
<!-- WiFi-CspMoreInfo-End -->

<!-- WiFi-End -->

## Related articles

[Configuration service provider reference](configuration-service-provider-reference.md)
