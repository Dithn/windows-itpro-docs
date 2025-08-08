---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## FIDO2

The FIDO Alliance, the Fast Identity Online industry standards body, was established to promote authentication technologies and standards that reduce reliance on passwords. FIDO Alliance and World Wide Web Consortium (W3C) worked together to define the Client to Authenticator Protocol (CTAP2) and Web Authentication (WebAuthn) specifications. These specifications are the industry standard for providing strong, phishing-resistant, user friendly, and privacy preserving authentication across the web and apps. FIDO standards and certifications are becoming recognized as the leading standard for creating secure authentication solutions across enterprises, governments, and consumer markets.

Windows 11 can also use external FIDO2 security keys for authentication alongside or in addition to Windows Hello and Windows Hello for Business, which is also a FIDO2-certified passwordless solution. As a result, Windows 11 can be used as a FIDO authenticator for many popular identity management services.

### Passkeys

Windows 11 makes it much harder for hackers who exploit stolen passwords via phishing attacks by empowering users to replace passwords with passkeys. Passkeys are the cross-platform future of secure sign-in. Microsoft and other technology leaders are supporting passkeys across their platforms and services.

A passkey is a unique, unguessable cryptographic secret that is securely stored on the device. Instead of using a username and password to sign in to a website or application, Windows 11 users can create and use a passkey with Windows Hello, a third-party passkey provider, an external FIDO2 security key, or their mobile device. Passkeys on Windows work in any browsers or apps that support them for sign in.

Passkeys created and saved with Windows Hello are protected by Windows Hello or Windows Hello for Business. Users can sign in to the site or app using their face, fingerprint, or device PIN. Users can manage their passkeys from **Settings** > **Accounts** > **Passkeys**.

:::row:::
    :::column span="2":::
[!INCLUDE [coming-soon](coming-soon.md)]

The plug-in model for third-party passkey providers enables users to manage their passkeys with third-party passkey managers. This model ensures a seamless platform experience, regardless of whether passkeys are managed directly by Windows or by a third-party authenticator. When a third-party passkey provider is used, the passkeys are securely protected and managed by the third-party provider.
    :::column-end:::
    :::column span="2":::
:::image type="content" border="false" source="../images/passkey-save-3p.png" alt-text="Screenshot of the save passkey dialog box showing third-party providers."  lightbox="../images/passkey-save-3p.png":::
    :::column-end:::
:::row-end:::

[!INCLUDE [learn-more](learn-more.md)]

- [Support for passkeys in Windows](/windows/security/identity-protection/passkeys)
- [Enable passkeys (FIDO2) for your organization](/entra/identity/authentication/how-to-enable-passkey-fido2)
