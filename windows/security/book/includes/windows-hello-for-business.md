---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## Windows Hello for Business

Windows Hello for Business extends Windows Hello to work with an organization's Active Directory and Microsoft Entra ID accounts. It provides single sign-on access to work or school resources such as OneDrive, work email, and other business apps. Windows Hello for Business also gives IT admins the ability to manage PIN and other sign-in requirements for devices connecting to work or school resources.

After Windows Hello for Business is provisioned, users can use a PIN, face, or fingerprint to unlock credentials and sign into their Windows device.

Provisioning methods include:

- Passkeys (preview), which provide a seamless way for users to authenticate to Microsoft Entra ID without entering a username or password
- Temporary Access Pass (TAP), a time-limited passcode with strong authentication requirements issued through Microsoft Entra ID
- Existing multifactor authentication with Microsoft Entra ID, including the Microsoft Authenticator app

Windows Hello for Business enhances security by replacing traditional usernames and passwords with a combination of a security key or certificate and a PIN or biometric data. This setup securely maps the credentials to a user account.

There are various deployment models available for Windows Hello for Business, providing flexibility to meet the diverse needs of different organizations. Among these, the *Hybrid cloud Kerberos trust* model is recommended and considered the simplest for organizations operating in hybrid environments.

[!INCLUDE [learn-more](learn-more.md)]

- [Windows Hello for Business overview](/windows/security/identity-protection/hello-for-business)
- [Enable passkeys (FIDO2) for your organization](/entra/identity/authentication/how-to-enable-passkey-fido2)

### PIN reset

The Microsoft PIN Reset Service allows users to reset their forgotten Windows Hello PINs without requiring re-enrollment. After registering the service in the Microsoft Entra ID tenant, the capability must be enabled on the Windows devices using group policy or a device management solution like Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup>.

Users can initiate a PIN reset from the Windows lock screen or from the sign-in options in Settings. The process involves authenticating and completing multifactor authentication to reset the PIN.

[!INCLUDE [learn-more](learn-more.md)]

- [PIN reset](/windows/security/identity-protection/hello-for-business/pin-reset)

### Multi-factor unlock

For organizations that need an extra layer of sign-in security, multi-factor unlock enables IT admins to configure Windows to require a combination of two unique trusted signals to sign in. Trusted signal examples include a PIN or biometric data (face or fingerprint) combined with either a PIN, Bluetooth, IP configuration, or Wi-Fi.

Multi-factor unlock is useful for organizations who need to prevent information workers from sharing credentials or need to comply with regulatory requirements for a two-factor authentication policy.

[!INCLUDE [learn-more](learn-more.md)]

- [Multi-factor unlock](/windows/security/identity-protection/hello-for-business/feature-multifactor-unlock)

### Windows passwordless experience

**Windows Hello for Business now support a fully passwordless experience.**

IT admins can configure a policy on Microsoft Entra ID joined machines so users no longer see the option to enter a password when accessing company resources. Once the policy is configured, passwords are removed from the Windows user experience, both for device unlock and in-session authentication scenarios. However, passwords aren't eliminated from the identity directory yet. Users are expected to navigate through their core authentication scenarios using strong, phish-resistant, possession-based credentials like Windows Hello for Business and FIDO2 security keys. If necessary, users can use passwordless recovery mechanisms such as Microsoft PIN reset service or web sign-in.

Users authenticate directly with Microsoft Entra ID, helping speed access to on-premises applications and other resources.

[!INCLUDE [learn-more](learn-more.md)]

- [Windows passwordless experience](/windows/security/identity-protection/passwordless-experience)
