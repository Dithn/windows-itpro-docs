---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## :::image type="icon" source="../images/azure-attestation.svg" border="false"::: Azure Attestation service

Remote attestation helps ensure that devices are compliant with security policies and are operating in a trusted state before they're allowed to access resources. Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup> integrates with Azure Attestation service to review Windows device health comprehensively and connect this information with Microsoft Entra ID<sup>[\[4\]](../conclusion.md#footnote4)</sup> Conditional Access.

**Attestation policies are configured in the Azure Attestation service which can then:**

- Verify the integrity of evidence provided by the Windows Attestation component by validating the signature and ensuring the Platform Configuration Registers (PCRs) match the values recomputed by replaying the measured boot log
- Verify that the TPM has a valid Attestation Identity Key issued by the authenticated TPM
- Verify that security features are in the expected states

Once this verification is complete, the attestation service returns a signed report with the security features state to the relying party - such as Microsoft Intune - to assess the trustworthiness of the platform relative to the admin-configured device compliance specifications. Conditional access is then granted or denied based on the device's compliance.

[!INCLUDE [learn-more](learn-more.md)]

- [Azure Attestation overview](/azure/attestation/overview)
