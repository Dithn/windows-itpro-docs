---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Enhanced Sign-in Security (ESS)

Windows Hello supports Enhanced Sign-in Security, which uses specialized hardware and software components to raise the security bar even higher for biometric sign-in.

Enhanced Sign-in Security biometrics uses Virtualization-based security (VBS) and the TPM to isolate user authentication processes and data and secure the pathway by which the information is communicated.

These specialized components protect against a class of attacks that includes biometric sample injection, replay, and tampering. For example, fingerprint readers must implement Secure Device Connection Protocol, which uses key negotiation and a Microsoft-issued certificate to protect and securely store user authentication data. For facial recognition, components such as the Secure Devices (SDEV) table and process isolation with trustlets help prevent more attack classes.

Enhanced Sign-in Security is configured by device manufacturers during the manufacturing process and is most typically supported in secured-core PCs. For facial recognition, Enhanced Sign-in Security is supported by specific silicon and camera combinations -  check with the specific device manufacturer. Fingerprint authentication is available across all processor types. Reach out to specific OEMs for support details.

[!INCLUDE [learn-more](learn-more.md)]

- [Windows Hello Enhanced Sign-in Security](/windows-hardware/design/device-experiences/windows-hello-enhanced-sign-in-security)
