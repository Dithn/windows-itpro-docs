---
title: LanmanWorkstation Policy CSP
description: Learn more about the LanmanWorkstation Area in Policy CSP.
ms.date: 07/22/2025
ms.topic: generated-reference
---

<!-- Auto-Generated CSP Document -->

<!-- LanmanWorkstation-Begin -->
# Policy CSP - LanmanWorkstation

[!INCLUDE [Windows Insider tip](includes/mdm-insider-csp-note.md)]

<!-- LanmanWorkstation-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- LanmanWorkstation-Editable-End -->

<!-- AuditInsecureGuestLogon-Begin -->
## AuditInsecureGuestLogon

<!-- AuditInsecureGuestLogon-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- AuditInsecureGuestLogon-Applicability-End -->

<!-- AuditInsecureGuestLogon-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanWorkstation/AuditInsecureGuestLogon
```
<!-- AuditInsecureGuestLogon-OmaUri-End -->

<!-- AuditInsecureGuestLogon-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls whether the SMB client will enable the audit event when the client is logged-on as guest account.

- If you enable this policy setting, the SMB client will log the event when the client is logged-on as guest account.

- If you disable or don't configure this policy setting, the SMB client won't log the event.
<!-- AuditInsecureGuestLogon-Description-End -->

<!-- AuditInsecureGuestLogon-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- AuditInsecureGuestLogon-Editable-End -->

<!-- AuditInsecureGuestLogon-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- AuditInsecureGuestLogon-DFProperties-End -->

<!-- AuditInsecureGuestLogon-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Disabled. |
| 1 | Enabled. |
<!-- AuditInsecureGuestLogon-AllowedValues-End -->

<!-- AuditInsecureGuestLogon-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | Pol_AuditInsecureGuestLogon |
| Friendly Name | Audit insecure guest logon |
| Location | Computer Configuration |
| Path | Network > Lanman Workstation |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanWorkstation |
| Registry Value Name | AuditInsecureGuestLogon |
| ADMX File Name | LanmanWorkstation.admx |
<!-- AuditInsecureGuestLogon-GpMapping-End -->

<!-- AuditInsecureGuestLogon-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- AuditInsecureGuestLogon-Examples-End -->

<!-- AuditInsecureGuestLogon-End -->

<!-- AuditServerDoesNotSupportEncryption-Begin -->
## AuditServerDoesNotSupportEncryption

<!-- AuditServerDoesNotSupportEncryption-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- AuditServerDoesNotSupportEncryption-Applicability-End -->

<!-- AuditServerDoesNotSupportEncryption-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanWorkstation/AuditServerDoesNotSupportEncryption
```
<!-- AuditServerDoesNotSupportEncryption-OmaUri-End -->

<!-- AuditServerDoesNotSupportEncryption-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls whether the SMB client will enable the audit event when the SMB server doesn't support encryption.

- If you enable this policy setting, the SMB client will log the event when the SMB server doesn't support encryption.

- If you disable or don't configure this policy setting, the SMB client won't log the event.
<!-- AuditServerDoesNotSupportEncryption-Description-End -->

<!-- AuditServerDoesNotSupportEncryption-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- AuditServerDoesNotSupportEncryption-Editable-End -->

<!-- AuditServerDoesNotSupportEncryption-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- AuditServerDoesNotSupportEncryption-DFProperties-End -->

<!-- AuditServerDoesNotSupportEncryption-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Disabled. |
| 1 | Enabled. |
<!-- AuditServerDoesNotSupportEncryption-AllowedValues-End -->

<!-- AuditServerDoesNotSupportEncryption-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | Pol_AuditServerDoesNotSupportEncryption |
| Friendly Name | Audit server does not support encryption |
| Location | Computer Configuration |
| Path | Network > Lanman Workstation |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanWorkstation |
| Registry Value Name | AuditServerDoesNotSupportEncryption |
| ADMX File Name | LanmanWorkstation.admx |
<!-- AuditServerDoesNotSupportEncryption-GpMapping-End -->

<!-- AuditServerDoesNotSupportEncryption-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- AuditServerDoesNotSupportEncryption-Examples-End -->

<!-- AuditServerDoesNotSupportEncryption-End -->

<!-- AuditServerDoesNotSupportSigning-Begin -->
## AuditServerDoesNotSupportSigning

<!-- AuditServerDoesNotSupportSigning-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- AuditServerDoesNotSupportSigning-Applicability-End -->

<!-- AuditServerDoesNotSupportSigning-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanWorkstation/AuditServerDoesNotSupportSigning
```
<!-- AuditServerDoesNotSupportSigning-OmaUri-End -->

<!-- AuditServerDoesNotSupportSigning-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls whether the SMB client will enable the audit event when the SMB server doesn't support signing.

- If you enable this policy setting, the SMB client will log the event when the SMB server doesn't support signing.

- If you disable or don't configure this policy setting, the SMB client won't log the event.
<!-- AuditServerDoesNotSupportSigning-Description-End -->

<!-- AuditServerDoesNotSupportSigning-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- AuditServerDoesNotSupportSigning-Editable-End -->

<!-- AuditServerDoesNotSupportSigning-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- AuditServerDoesNotSupportSigning-DFProperties-End -->

<!-- AuditServerDoesNotSupportSigning-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Disabled. |
| 1 | Enabled. |
<!-- AuditServerDoesNotSupportSigning-AllowedValues-End -->

<!-- AuditServerDoesNotSupportSigning-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | Pol_AuditServerDoesNotSupportSigning |
| Friendly Name | Audit server does not support signing |
| Location | Computer Configuration |
| Path | Network > Lanman Workstation |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanWorkstation |
| Registry Value Name | AuditServerDoesNotSupportSigning |
| ADMX File Name | LanmanWorkstation.admx |
<!-- AuditServerDoesNotSupportSigning-GpMapping-End -->

<!-- AuditServerDoesNotSupportSigning-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- AuditServerDoesNotSupportSigning-Examples-End -->

<!-- AuditServerDoesNotSupportSigning-End -->

<!-- EnableInsecureGuestLogons-Begin -->
## EnableInsecureGuestLogons

<!-- EnableInsecureGuestLogons-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 10, version 1803 [10.0.17134] and later |
<!-- EnableInsecureGuestLogons-Applicability-End -->

<!-- EnableInsecureGuestLogons-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanWorkstation/EnableInsecureGuestLogons
```
<!-- EnableInsecureGuestLogons-OmaUri-End -->

<!-- EnableInsecureGuestLogons-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy setting determines if the SMB client will allow insecure guest logons to an SMB server.

- If you enable this policy setting or if you don't configure this policy setting, the SMB client will allow insecure guest logons.

- If you disable this policy setting, the SMB client will reject insecure guest logons.

If you enable signing, the SMB client will reject insecure guest logons.

Insecure guest logons are used by file servers to allow unauthenticated access to shared folders. While uncommon in an enterprise environment, insecure guest logons are frequently used by consumer Network Attached Storage (NAS) appliances acting as file servers. Windows file servers require authentication and don't use insecure guest logons by default. Since insecure guest logons are unauthenticated, important security features such as SMB Signing and SMB Encryption are disabled. As a result, clients that allow insecure guest logons are vulnerable to a variety of man-in-the-middle attacks that can result in data loss, data corruption, and exposure to malware. Additionally, any data written to a file server using an insecure guest logon is potentially accessible to anyone on the network. Microsoft recommends disabling insecure guest logons and configuring file servers to require authenticated access".
<!-- EnableInsecureGuestLogons-Description-End -->

<!-- EnableInsecureGuestLogons-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- EnableInsecureGuestLogons-Editable-End -->

<!-- EnableInsecureGuestLogons-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- EnableInsecureGuestLogons-DFProperties-End -->

<!-- EnableInsecureGuestLogons-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Disabled. |
| 1 | Enabled. |
<!-- EnableInsecureGuestLogons-AllowedValues-End -->

<!-- EnableInsecureGuestLogons-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | Pol_EnableInsecureGuestLogons |
| Friendly Name | Enable insecure guest logons |
| Location | Computer Configuration |
| Path | Network > Lanman Workstation |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanWorkstation |
| Registry Value Name | AllowInsecureGuestAuth |
| ADMX File Name | LanmanWorkstation.admx |
<!-- EnableInsecureGuestLogons-GpMapping-End -->

<!-- EnableInsecureGuestLogons-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- EnableInsecureGuestLogons-Examples-End -->

<!-- EnableInsecureGuestLogons-End -->

<!-- EnableMailslots-Begin -->
## EnableMailslots

<!-- EnableMailslots-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- EnableMailslots-Applicability-End -->

<!-- EnableMailslots-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanWorkstation/EnableMailslots
```
<!-- EnableMailslots-OmaUri-End -->

<!-- EnableMailslots-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls whether the SMB client will enable or disable remote mailslots over MUP.

- If you disable this policy setting, remote mailslots won't function over MUP, hence they won't go through the SMB client redirector.

- If you don't configure this policy setting, remote mailslots may be allowed through MUP.
<!-- EnableMailslots-Description-End -->

<!-- EnableMailslots-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- EnableMailslots-Editable-End -->

<!-- EnableMailslots-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- EnableMailslots-DFProperties-End -->

<!-- EnableMailslots-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Disabled. |
| 1 | Enabled. |
<!-- EnableMailslots-AllowedValues-End -->

<!-- EnableMailslots-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | Pol_EnableMailslots |
| Friendly Name | Enable remote mailslots |
| Location | Computer Configuration |
| Path | Network > Lanman Workstation |
| Registry Key Name | Software\Policies\Microsoft\Windows\NetworkProvider |
| Registry Value Name | EnableMailslots |
| ADMX File Name | LanmanWorkstation.admx |
<!-- EnableMailslots-GpMapping-End -->

<!-- EnableMailslots-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- EnableMailslots-Examples-End -->

<!-- EnableMailslots-End -->

<!-- MaxSmb2Dialect-Begin -->
## MaxSmb2Dialect

<!-- MaxSmb2Dialect-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- MaxSmb2Dialect-Applicability-End -->

<!-- MaxSmb2Dialect-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanWorkstation/MaxSmb2Dialect
```
<!-- MaxSmb2Dialect-OmaUri-End -->

<!-- MaxSmb2Dialect-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls the maximum version of SMB protocol.

> [!NOTE]
> This group policy doesn't prevent use of SMB 1 if that component is still installed and enabled.
<!-- MaxSmb2Dialect-Description-End -->

<!-- MaxSmb2Dialect-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- MaxSmb2Dialect-Editable-End -->

<!-- MaxSmb2Dialect-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 785 |
<!-- MaxSmb2Dialect-DFProperties-End -->

<!-- MaxSmb2Dialect-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 514 | SMB 2.0.2. |
| 528 | SMB 2.1.0. |
| 768 | SMB 3.0.0. |
| 770 | SMB 3.0.2. |
| 785 (Default) | SMB 3.1.1. |
<!-- MaxSmb2Dialect-AllowedValues-End -->

<!-- MaxSmb2Dialect-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | Pol_MaxSmb2Dialect |
| Friendly Name | Mandate the maximum version of SMB |
| Location | Computer Configuration |
| Path | Network > Lanman Workstation |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanWorkstation |
| ADMX File Name | LanmanWorkstation.admx |
<!-- MaxSmb2Dialect-GpMapping-End -->

<!-- MaxSmb2Dialect-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- MaxSmb2Dialect-Examples-End -->

<!-- MaxSmb2Dialect-End -->

<!-- MinSmb2Dialect-Begin -->
## MinSmb2Dialect

<!-- MinSmb2Dialect-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- MinSmb2Dialect-Applicability-End -->

<!-- MinSmb2Dialect-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanWorkstation/MinSmb2Dialect
```
<!-- MinSmb2Dialect-OmaUri-End -->

<!-- MinSmb2Dialect-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls the minimum version of SMB protocol.

> [!NOTE]
> This group policy doesn't prevent use of SMB 1 if that component is still installed and enabled.
<!-- MinSmb2Dialect-Description-End -->

<!-- MinSmb2Dialect-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- MinSmb2Dialect-Editable-End -->

<!-- MinSmb2Dialect-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 514 |
<!-- MinSmb2Dialect-DFProperties-End -->

<!-- MinSmb2Dialect-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 514 (Default) | SMB 2.0.2. |
| 528 | SMB 2.1.0. |
| 768 | SMB 3.0.0. |
| 770 | SMB 3.0.2. |
| 785 | SMB 3.1.1. |
<!-- MinSmb2Dialect-AllowedValues-End -->

<!-- MinSmb2Dialect-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | Pol_MinSmb2Dialect |
| Friendly Name | Mandate the minimum version of SMB |
| Location | Computer Configuration |
| Path | Network > Lanman Workstation |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanWorkstation |
| ADMX File Name | LanmanWorkstation.admx |
<!-- MinSmb2Dialect-GpMapping-End -->

<!-- MinSmb2Dialect-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- MinSmb2Dialect-Examples-End -->

<!-- MinSmb2Dialect-End -->

<!-- RequireEncryption-Begin -->
## RequireEncryption

<!-- RequireEncryption-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- RequireEncryption-Applicability-End -->

<!-- RequireEncryption-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanWorkstation/RequireEncryption
```
<!-- RequireEncryption-OmaUri-End -->

<!-- RequireEncryption-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls whether the SMB client will require encryption.

- If you enable this policy setting, the SMB client will require the SMB server to support encryption and encrypt the data.

- If you disable or don't configure this policy setting, the SMB client won't require encryption. However, SMB encryption may still be required; see notes below.

> [!NOTE]
> This policy is combined with per-share, per-server, and per mapped drive connection properties, through which SMB encryption may be required. The SMB server must support and enable SMB encryption. For example, should this policy be disabled (or not configured), the SMB client may still perform encryption if an SMB server share has required encryption.

> [!IMPORTANT]
> SMB encryption requires SMB 3.0 or later.
<!-- RequireEncryption-Description-End -->

<!-- RequireEncryption-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- RequireEncryption-Editable-End -->

<!-- RequireEncryption-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- RequireEncryption-DFProperties-End -->

<!-- RequireEncryption-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Disabled. |
| 1 | Enabled. |
<!-- RequireEncryption-AllowedValues-End -->

<!-- RequireEncryption-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | Pol_RequireEncryption |
| Friendly Name | Require Encryption |
| Location | Computer Configuration |
| Path | Network > Lanman Workstation |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanWorkstation |
| Registry Value Name | RequireEncryption |
| ADMX File Name | LanmanWorkstation.admx |
<!-- RequireEncryption-GpMapping-End -->

<!-- RequireEncryption-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- RequireEncryption-Examples-End -->

<!-- RequireEncryption-End -->

<!-- LanmanWorkstation-CspMoreInfo-Begin -->
<!-- Add any additional information about this CSP here. Anything outside this section will get overwritten. -->
<!-- LanmanWorkstation-CspMoreInfo-End -->

<!-- LanmanWorkstation-End -->

## Related articles

[Policy configuration service provider](policy-configuration-service-provider.md)
