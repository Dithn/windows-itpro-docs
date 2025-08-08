---
title: LanmanServer Policy CSP
description: Learn more about the LanmanServer Area in Policy CSP.
ms.date: 07/22/2025
ms.topic: generated-reference
---

<!-- Auto-Generated CSP Document -->

<!-- LanmanServer-Begin -->
# Policy CSP - LanmanServer

[!INCLUDE [Windows Insider tip](includes/mdm-insider-csp-note.md)]

<!-- LanmanServer-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- LanmanServer-Editable-End -->

<!-- AuditClientDoesNotSupportEncryption-Begin -->
## AuditClientDoesNotSupportEncryption

<!-- AuditClientDoesNotSupportEncryption-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- AuditClientDoesNotSupportEncryption-Applicability-End -->

<!-- AuditClientDoesNotSupportEncryption-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanServer/AuditClientDoesNotSupportEncryption
```
<!-- AuditClientDoesNotSupportEncryption-OmaUri-End -->

<!-- AuditClientDoesNotSupportEncryption-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls whether the SMB server will log the event when the SMB client doesn't support encryption.

- If you enable this policy setting, the SMB server will log the event when the SMB client doesn't support encryption.

- If you disable or don't configure this policy setting, the SMB server won't log the event.
<!-- AuditClientDoesNotSupportEncryption-Description-End -->

<!-- AuditClientDoesNotSupportEncryption-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- AuditClientDoesNotSupportEncryption-Editable-End -->

<!-- AuditClientDoesNotSupportEncryption-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- AuditClientDoesNotSupportEncryption-DFProperties-End -->

<!-- AuditClientDoesNotSupportEncryption-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Disabled. |
| 1 | Enabled. |
<!-- AuditClientDoesNotSupportEncryption-AllowedValues-End -->

<!-- AuditClientDoesNotSupportEncryption-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | Pol_AuditClientDoesNotSupportEncryption |
| Friendly Name | Audit client does not support encryption |
| Location | Computer Configuration |
| Path | Network > Lanman Server |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanServer |
| Registry Value Name | AuditClientDoesNotSupportEncryption |
| ADMX File Name | LanmanServer.admx |
<!-- AuditClientDoesNotSupportEncryption-GpMapping-End -->

<!-- AuditClientDoesNotSupportEncryption-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- AuditClientDoesNotSupportEncryption-Examples-End -->

<!-- AuditClientDoesNotSupportEncryption-End -->

<!-- AuditClientDoesNotSupportSigning-Begin -->
## AuditClientDoesNotSupportSigning

<!-- AuditClientDoesNotSupportSigning-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- AuditClientDoesNotSupportSigning-Applicability-End -->

<!-- AuditClientDoesNotSupportSigning-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanServer/AuditClientDoesNotSupportSigning
```
<!-- AuditClientDoesNotSupportSigning-OmaUri-End -->

<!-- AuditClientDoesNotSupportSigning-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls whether the SMB server will log the event when the SMB client doesn't support signing.

If you enable this policy setting, the SMB server will log the event when the SMB client doesn't support signing.
<!-- AuditClientDoesNotSupportSigning-Description-End -->

<!-- AuditClientDoesNotSupportSigning-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- AuditClientDoesNotSupportSigning-Editable-End -->

<!-- AuditClientDoesNotSupportSigning-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 0 |
<!-- AuditClientDoesNotSupportSigning-DFProperties-End -->

<!-- AuditClientDoesNotSupportSigning-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 (Default) | Disabled. |
| 1 | Enabled. |
<!-- AuditClientDoesNotSupportSigning-AllowedValues-End -->

<!-- AuditClientDoesNotSupportSigning-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | Pol_AuditClientDoesNotSupportSigning |
| Friendly Name | Audit client does not support signing |
| Location | Computer Configuration |
| Path | Network > Lanman Server |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanServer |
| Registry Value Name | AuditClientDoesNotSupportSigning |
| ADMX File Name | LanmanServer.admx |
<!-- AuditClientDoesNotSupportSigning-GpMapping-End -->

<!-- AuditClientDoesNotSupportSigning-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- AuditClientDoesNotSupportSigning-Examples-End -->

<!-- AuditClientDoesNotSupportSigning-End -->

<!-- AuditInsecureGuestLogon-Begin -->
## AuditInsecureGuestLogon

<!-- AuditInsecureGuestLogon-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- AuditInsecureGuestLogon-Applicability-End -->

<!-- AuditInsecureGuestLogon-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanServer/AuditInsecureGuestLogon
```
<!-- AuditInsecureGuestLogon-OmaUri-End -->

<!-- AuditInsecureGuestLogon-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls whether the SMB server will enable the audit event when the client is logged-on as guest account.

- If you enable this policy setting, the SMB server will log the event when the client is logged-on as guest account.

- If you disable or don't configure this policy setting, the SMB server won't log the event.
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
| Path | Network > Lanman Server |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanServer |
| Registry Value Name | AuditInsecureGuestLogon |
| ADMX File Name | LanmanServer.admx |
<!-- AuditInsecureGuestLogon-GpMapping-End -->

<!-- AuditInsecureGuestLogon-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- AuditInsecureGuestLogon-Examples-End -->

<!-- AuditInsecureGuestLogon-End -->

<!-- AuthRateLimiterDelayInMs-Begin -->
## AuthRateLimiterDelayInMs

<!-- AuthRateLimiterDelayInMs-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- AuthRateLimiterDelayInMs-Applicability-End -->

<!-- AuthRateLimiterDelayInMs-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanServer/AuthRateLimiterDelayInMs
```
<!-- AuthRateLimiterDelayInMs-OmaUri-End -->

<!-- AuthRateLimiterDelayInMs-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls whether the SMB server will use a default value in milliseconds for the invalid authentication delay.

- If you configure this policy setting, the authentication rate limiter will use the specified value for delaying invalid authentication attempts.

- If you don't configure this policy setting, the authentication rate limiter will use the default value or the value from local registry under HKLM\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters.
<!-- AuthRateLimiterDelayInMs-Description-End -->

<!-- AuthRateLimiterDelayInMs-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- AuthRateLimiterDelayInMs-Editable-End -->

<!-- AuthRateLimiterDelayInMs-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Allowed Values | Range: `[0-10000]` |
| Default Value  | 2000 |
<!-- AuthRateLimiterDelayInMs-DFProperties-End -->

<!-- AuthRateLimiterDelayInMs-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | Pol_AuthRateLimiterDelayInMs |
| Friendly Name | Set authentication rate limiter delay (milliseconds) |
| Location | Computer Configuration |
| Path | Network > Lanman Server |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanServer |
| ADMX File Name | LanmanServer.admx |
<!-- AuthRateLimiterDelayInMs-GpMapping-End -->

<!-- AuthRateLimiterDelayInMs-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- AuthRateLimiterDelayInMs-Examples-End -->

<!-- AuthRateLimiterDelayInMs-End -->

<!-- EnableAuthRateLimiter-Begin -->
## EnableAuthRateLimiter

<!-- EnableAuthRateLimiter-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- EnableAuthRateLimiter-Applicability-End -->

<!-- EnableAuthRateLimiter-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanServer/EnableAuthRateLimiter
```
<!-- EnableAuthRateLimiter-OmaUri-End -->

<!-- EnableAuthRateLimiter-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls whether the SMB server will enable or disable the authentication rate limiter.

- If you disable this policy setting, the authentication rate limiter won't be enabled.

- If you don't configure this policy setting, the authentication rate limiter may still be working depending on the delay settings (the recommended delay value is 2000ms).
<!-- EnableAuthRateLimiter-Description-End -->

<!-- EnableAuthRateLimiter-Editable-Begin -->
<!-- Add any additional information about this policy here. Anything outside this section will get overwritten. -->
<!-- EnableAuthRateLimiter-Editable-End -->

<!-- EnableAuthRateLimiter-DFProperties-Begin -->
**Description framework properties**:

| Property name | Property value |
|:--|:--|
| Format | `int` |
| Access Type | Add, Delete, Get, Replace |
| Default Value  | 1 |
<!-- EnableAuthRateLimiter-DFProperties-End -->

<!-- EnableAuthRateLimiter-AllowedValues-Begin -->
**Allowed values**:

| Value | Description |
|:--|:--|
| 0 | Disabled. |
| 1 (Default) | Enabled. |
<!-- EnableAuthRateLimiter-AllowedValues-End -->

<!-- EnableAuthRateLimiter-GpMapping-Begin -->
**Group policy mapping**:

| Name | Value |
|:--|:--|
| Name | Pol_EnableAuthRateLimiter |
| Friendly Name | Enable authentication rate limiter |
| Location | Computer Configuration |
| Path | Network > Lanman Server |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanServer |
| Registry Value Name | EnableAuthRateLimiter |
| ADMX File Name | LanmanServer.admx |
<!-- EnableAuthRateLimiter-GpMapping-End -->

<!-- EnableAuthRateLimiter-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- EnableAuthRateLimiter-Examples-End -->

<!-- EnableAuthRateLimiter-End -->

<!-- EnableMailslots-Begin -->
## EnableMailslots

<!-- EnableMailslots-Applicability-Begin -->
| Scope | Editions | Applicable OS |
|:--|:--|:--|
| ✅ Device <br> ❌ User | ✅ Pro <br> ✅ Enterprise <br> ✅ Education <br> ✅ IoT Enterprise / IoT Enterprise LTSC | ✅ Windows 11, version 24H2 [10.0.26100.3613] and later |
<!-- EnableMailslots-Applicability-End -->

<!-- EnableMailslots-OmaUri-Begin -->
```Device
./Device/Vendor/MSFT/Policy/Config/LanmanServer/EnableMailslots
```
<!-- EnableMailslots-OmaUri-End -->

<!-- EnableMailslots-Description-Begin -->
<!-- Description-Source-ADMX -->
This policy controls whether the SMB server will enable or disable remote mailslots over the computer browser service.

- If you disable this policy setting, the computer browser service will no longer run as expected.

- If you don't configure this policy setting, the computer browser may still be working with remote mailslots enabled.

> [!NOTE]
> This policy requires a Windows reboot to take effect.
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
| Path | Network > Lanman Server |
| Registry Key Name | Software\Policies\Microsoft\Windows\Bowser |
| Registry Value Name | EnableMailslots |
| ADMX File Name | LanmanServer.admx |
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
./Device/Vendor/MSFT/Policy/Config/LanmanServer/MaxSmb2Dialect
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
| Path | Network > Lanman Server |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanServer |
| ADMX File Name | LanmanServer.admx |
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
./Device/Vendor/MSFT/Policy/Config/LanmanServer/MinSmb2Dialect
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
| Path | Network > Lanman Server |
| Registry Key Name | Software\Policies\Microsoft\Windows\LanmanServer |
| ADMX File Name | LanmanServer.admx |
<!-- MinSmb2Dialect-GpMapping-End -->

<!-- MinSmb2Dialect-Examples-Begin -->
<!-- Add any examples for this policy here. Examples outside this section will get overwritten. -->
<!-- MinSmb2Dialect-Examples-End -->

<!-- MinSmb2Dialect-End -->

<!-- LanmanServer-CspMoreInfo-Begin -->
<!-- Add any additional information about this CSP here. Anything outside this section will get overwritten. -->
<!-- LanmanServer-CspMoreInfo-End -->

<!-- LanmanServer-End -->

## Related articles

[Policy configuration service provider](policy-configuration-service-provider.md)
