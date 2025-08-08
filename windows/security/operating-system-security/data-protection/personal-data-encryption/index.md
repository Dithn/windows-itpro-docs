---
title: Personal Data Encryption Overview
description: Learn about Personal Data Encryption, a security feature that provides file-based data encryption capabilities to Windows.
ms.topic: overview
ms.date: 03/12/2025
---

# Personal Data Encryption overview

Personal Data Encryption is a security feature that provides file-based data encryption capabilities to Windows. It utilizes Windows Hello for Business to link *data encryption keys* with user credentials. When a user signs in to a device using Windows Hello, decryption keys are released, and encrypted data becomes accessible to the user. Conversely, when a user signs out, decryption keys are discarded, rendering the data inaccessible even if another user signs into the device. This ensures that sensitive information remains always protected.

The benefits of Personal Data Encryption are significant. By reducing the number of credentials needed to access encrypted content, users only need to sign in with Windows Hello. Additionally, the accessibility features available with Windows Hello extend to Personal Data Encryption protected content.

Unlike BitLocker, which encrypts entire volumes and disks, Personal Data Encryption focuses on individual files, providing another layer of security. This feature not only enhances data protection but also shows a strong commitment to safeguarding personal information.

## Personal Data Encryption for known folders

:::row:::
  :::column span="2":::
  Starting in Windows 11, version 24H2, Personal Data Encryption is further enhanced with *Personal Data Encryption for known folders*. Once enabled, the Windows folders **Desktop**, **Documents**, and **Pictures**, along with their contents, are automatically encrypted. This feature provides a quick and easy way to add an extra layer of security to commonly used folders.
  :::column-end:::
  :::column span="2":::
  :::image type="content" source="images/pde-known-folders.png" alt-text="Icons of the known folders with a padlock representing their encryption status." border="false":::
  :::column-end:::
:::row-end:::

## Prerequisites

To use Personal Data Encryption, the following prerequisites must be met:

- Windows 11, version 22H2 and later.
  - Personal Data Encryption for known folders is only available on Windows 11, version 24H2 and later.
- The devices must be [Microsoft Entra joined][ENTRA-1] or [Microsoft Entra hybrid joined][ENTRA-2]. Domain-joined devices aren't supported.
- Users must sign in using [Windows Hello](../../../identity-protection/hello-for-business/index.md).
- [Automatic Restart Sign On (ARSO)](/windows-server/identity/ad-ds/manage/component-updates/winlogon-automatic-restart-sign-on--arso-) must be disabled.

> [!IMPORTANT]
> If you sign in with a password or a [FIDO2 security key][ENTRA-3], you can't access Personal Data Encryption protected content.

> [!NOTE]
> When prerequisites aren't satisfied, the system falls back to [Data Protection API (DPAPI)](/dotnet/standard/security/how-to-use-data-protection).

[!INCLUDE [personal-data-encryption-pde](../../../../../includes/licensing/personal-data-encryption-pde.md)]

## Personal Data Encryption protection levels

Personal Data Encryption uses *AES-CBC* with a *256-bit key* to protect content and offers two levels of protection. The level of protection is determined based on the organizational needs. These levels can be set via the [Personal Data Encryption APIs](/uwp/api/windows.security.dataprotection.userdataprotectionmanager).

| Item | Level 1 | Level 2 |
|---|---|---|
| Protected data accessible when user signs in via Windows Hello | Yes | Yes |
| Protected data is accessible at Windows lock screen | Yes | Data is accessible for one minute after lock, then it's no longer available |
| Protected data is accessible after user signs out of Windows | No | No |
| Protected data is accessible when device is shut down | No | No |
| Protected data is accessible via UNC paths | No | No |
| Protected data is accessible when signing with Windows password instead of Windows Hello | No | No |
| Protected data is accessible via Remote Desktop session | No | No |
| Decryption keys used by Personal Data Encryption discarded | After user signs out of Windows | One minute after Windows lock screen is engaged or after user signs out of Windows |

## Personal Data Encryption protected content accessibility

When a file is protected with Personal Data Encryption, its icon shows a padlock. If the user isn't signed in locally with Windows Hello, or an unauthorized user attempts to access protected content, they're denied access.

Scenarios where a user is denied access to Personal Data Encryption protected content include:

- User signs in with a password instead of using Windows Hello (biometrics or PIN)
- If protected via level 2 protection, when the device is locked
- When trying to access content on the device remotely. For example, UNC network paths
- Remote Desktop sessions
- Other users on the device who aren't owners of the content, even if they're signed in via Windows Hello and have permissions to navigate to the Personal Data Encryption protected content

## Differences between Personal Data Encryption and BitLocker

Personal Data Encryption is meant to work alongside BitLocker. Personal Data Encryption isn't a replacement for BitLocker, nor is BitLocker a replacement for Personal Data Encryption. Using both features together provides better security than using either BitLocker or Personal Data Encryption alone. However there are differences between BitLocker and Personal Data Encryption and how they work. These differences are why using them together offers better security.

|| Personal Data Encryption | BitLocker |
|--|--|--|
| **Release of decryption key**| At user sign-in via Windows Hello | At boot |
| **Decryption keys discarded**| When user signs out of Windows or one minute after Windows lock screen is engaged | At shutdown |
| **Protected content**| All files in protected folders | Entire volume/drive |
| **Authentication to access protected content**| Windows Hello for Business | When BitLocker with TPM + PIN is enabled, BitLocker PIN plus Windows sign-in |

## Differences between Personal Data Encryption and EFS

The main difference between protecting files with Personal Data Encryption instead of EFS is the method they use to protect the file. Personal Data Encryption uses Windows Hello for Business to secure the keys that protect the files. EFS uses certificates to secure and protect the files.

To see if a file is protected with Personal Data Encryption or with EFS:

1. Open the properties of the file
1. Under the **General** tab, select **Advanced...**
1. In the **Advanced Attributes** windows, select **Details**

For Personal Data Encryption protected files, under **Protection status:** there's an item listed as **Personal Data Encryption is: On**.

For EFS protected files, under **Users who can access this file:**, there's a **Certificate thumbprint** next to the users with access to the file. There's also a section labeled **Recovery certificates for this file as defined by recovery policy:**.

Encryption information including what encryption method is being used to protect the file can be obtained with the [`cipher.exe /c`](/windows-server/administration/windows-commands/cipher) command.

## Recommendations for using Personal Data Encryption

The following are recommendations for using Personal Data Encryption:

- Enable [BitLocker Drive Encryption](../bitlocker/index.md). Although Personal Data Encryption works without BitLocker, it's recommended to enable BitLocker. Personal Data Encryption is meant to work alongside BitLocker for increased security at it isn't a replacement for BitLocker
- Backup solution such as [OneDrive in Microsoft 365](/sharepoint/onedrive-overview). In certain scenarios, such as TPM resets or destructive PIN resets, the keys used by Personal Data Encryption to protect content will be lost making any protected content inaccessible. The only way to recover such content is from a backup. If the files are synced to OneDrive, to regain access you must resync OneDrive
- [Windows Hello for Business PIN reset service](../../../identity-protection/hello-for-business/hello-feature-pin-reset.md). Destructive PIN reset causes keys used by Personal Data Encryption to protect content to be lost, making any content protected with Personal Data Encryption inaccessible. After a destructive PIN reset, content protected with Personal Data Encryption must be recovered from a backup. For this reason, Windows Hello for Business PIN reset service is recommended since it provides nondestructive PIN resets
- [Windows Hello Enhanced Sign-in Security](/windows-hardware/design/device-experiences/windows-hello-enhanced-sign-in-security) offers more security when authenticating with Windows Hello via biometrics or PIN

## Next steps

- Learn about the available options to configure Personal Data Encryption and how to configure them via Microsoft Intune or configuration Service Provider (CSP): [Personal Data Encryption settings and configuration](configure.md)
- Review the [Personal Data Encryption FAQ](faq.yml)

<!--links used in this document-->

[ENTRA-1]: /entra/identity/devices/concept-directory-join
[ENTRA-2]: /entra/identity/devices/concept-hybrid-join
[ENTRA-3]: /entra/identity/authentication/howto-authentication-passwordless-security-key-windows#sign-in-with-fido2-security-key
