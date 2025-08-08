---
author: paolomatarazzo
ms.author: paoloma
ms.date: 03/12/2024
ms.topic: include
---

### History

This setting specifies the number of past PINs that can be associated to a user account that can't be reused. This policy enhances security by ensuring that old PINs are not reused continually. The value must be between 0 to 50 PINs. If this policy is set to 0, then storage of previous PINs is not required.

The default value is 0.

> [!NOTE]
> PIN history is not preserved through PIN reset.

|  | Path |
|--|--|
| **CSP** | `./Device/Vendor/MSFT/PassportForWork/{TenantId}/Policies/PINComplexity/`[devicetenantidpoliciespincomplexityhistory](/windows/client-management/mdm/passportforwork-csp#devicetenantidpoliciespincomplexityhistory)<br><br>`./User/Vendor/MSFT/PassportForWork/{TenantId}/Policies/PINComplexity/`[usertenantidpoliciespincomplexityhistory](/windows/client-management/mdm/passportforwork-csp#usertenantidpoliciespincomplexityhistory) |
| **GPO** | **Computer Configuration** > **Administrative Templates** > **System** > **PIN Complexity** |

> [!IMPORTANT]
> PIN history is not supported on:
>
> - Devices with [Enhanced Sign-in Security (ESS)](/windows-hardware/design/device-experiences/windows-hello-enhanced-sign-in-security) enabled, since Windows Hello uses Virtualization-based Security (VBS) to isolate credentials.
> - Starting with Windows 11, version 24H2, on all devices that have VBS enabled.
