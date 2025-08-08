---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Windows Hello

Too often, passwords are weak, stolen, or forgotten. Organizations are moving toward passwordless sign-in to reduce the risk of breaches, lower the cost of managing passwords, and improve productivity and satisfaction for their users and customers. Microsoft is committed to helping organizations move toward a secure, passwordless future with Windows Hello, a cornerstone of Windows security and identity protection.

Windows Hello can enable passwordless sign-in using biometric or PIN verification and provides built-in support for the FIDO2 passwordless industry standard. As a result, people no longer need to carry external hardware like a security key for authentication.

The secure, convenient sign-in experience can augment or replace passwords with a stronger authentication model based on a PIN or biometric data such as facial or fingerprint recognition secured by the Trusted Platform Module (TPM). Step-by-step guidance makes setup easy.

Using asymmetric keys provisioned in the TPM, Windows Hello protects authentication by binding a user's credentials to their device. Windows Hello validates the user based on either a PIN or biometrics match and only then allows the use of cryptographic keys bound to that user in the TPM.

PIN and biometric data stay on the device and can't be stored or accessed externally. Since the data can't be accessed by anyone without physical access to the device, credentials are protected against replay attacks, phishing, and spoofing as well as password reuse and leaks.

Windows Hello can authenticate users to a Microsoft account (MSA), identity provider services, or the relying parties that also implement the FIDO2 or WebAuthn standards.

[!INCLUDE [learn-more](learn-more.md)]

- [Configure Windows Hello](https://support.microsoft.com/topic/dae28983-8242-bb2a-d3d1-87c9d265a5f0)

### Windows Hello PIN

The Windows Hello PIN, which can only be entered by someone with physical access to the device, can be used for strong multifactor authentication. The PIN is protected by the TPM and, like biometric data, never leaves the device. When a user enters their PIN, an authentication key is unlocked and used to sign a request sent to the authenticating server.

The TPM protects against threats including PIN brute-force attacks on lost or stolen devices. After too many incorrect guesses, the device locks. IT admins can set security policies for PINs, such as complexity, length, and expiration requirements.

[!INCLUDE [new-24h2](new-24h2.md)]

If your device doesn't have built-in biometrics, Windows Hello has been enhanced to use Virtualization-based Security (VBS) by default to isolate credentials. This added layer of protection helps guard against admin-level attacks. Even when you sign in with a PIN, your credentials are stored in a secure container, ensuring protection on devices with or without built-in biometric sensors.

### Windows Hello biometric

Windows Hello biometric sign-in enhances both security and productivity with a quick and convenient sign-in experience. There's no need to enter your PIN; just use your biometric data for an easy and delightful sign-in.

Windows devices that support biometric hardware, such as fingerprint or facial recognition cameras, integrate directly with Windows Hello, enabling access to Windows client resources and services. Biometric readers for both face and fingerprint must comply with Windows Hello biometric requirements. Windows Hello facial recognition is designed to authenticate only from trusted cameras used at the time of enrollment.

If a peripheral camera is attached to the device after enrollment, it can be used for facial authentication once validated by signing in with the internal camera. For added security, external cameras can be disabled for use with Windows Hello facial recognition.

[!INCLUDE [learn-more](learn-more.md)]

- [Windows Hello biometric requirements](/windows-hardware/design/device-experiences/windows-hello-biometric-requirements)
