---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Device Health Attestation

The Windows Device Health Attestation process supports a Zero Trust paradigm that shifts the focus from static, network-based perimeters to users, assets, and resources. The attestation process confirms the device, firmware, and boot process are in a good state and haven't been tampered with before they can access corporate resources. These determinations are made with data stored in the TPM, which provides a secure root-of-trust. The information is sent to an attestation service such as Azure Attestation to verify that the device is in a trusted state. Then a cloud-native device management solution like Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup> reviews device health and connects this information with Microsoft Entra ID<sup>[\[4\]](../conclusion.md#footnote4)</sup> for conditional access.

Windows includes many security features to help protect users from malware and attacks. However, security components are trustworthy only if the platform boots as expected and isn't tampered with. As noted above, Windows relies on Unified Extensible Firmware Interface (UEFI) Secure Boot, ELAM, DRTM, Trusted Boot, and other low-level hardware and firmware security features to protect your PC from attacks. From the moment you power on your PC until your anti-malware starts, Windows is backed with the appropriate hardware configurations that help keep you safe. Measured Boot, implemented by bootloaders and BIOS, verifies and cryptographically records each step of the boot in a chained manner. These events are bound to the TPM, that functions as a hardware root-of-trust. Remote attestation is the mechanism by which these events are read and verified by a service to provide a verifiable, unbiased, and tamper-resilient report. Remote attestation is the trusted auditor of your system's boot, allowing reliant parties to bind trust to the device and its security.

A summary of the steps involved in attestation and Zero-Trust on a Windows device are as follows:

- During each step of the boot process - such as a file load, update of special variables, and more - information such as file hashes and signature(s) are measured in the TPM Platform Configuration Register (PCRs). The measurements are bound by a Trusted Computing Group specification that dictates which events can be recorded and the format of each event. The data provides important information about device security from the moment it powers on
- Once Windows has booted, the attestor (or verifier) requests the TPM get the measurements stored in its PCRs alongside the Measured Boot log. Together, these form the attestation evidence that's sent to the Azure Attestation service
- The TPM is verified by using the keys or cryptographic material available on the chipset with an Azure Certificate Service
- The above information is sent to the Azure Attestation Service to verify that the device is in a trusted state.

[!INCLUDE [learn-more](learn-more.md)]

- [Control the health of Windows devices](/windows/security/operating-system-security/system-security/protect-high-value-assets-by-controlling-the-health-of-windows-10-based-devices)
