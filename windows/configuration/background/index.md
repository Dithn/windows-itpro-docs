---
title: Configure the Desktop and Lock Screen Backgrounds in Windows
description: Learn how to configure the desktop and lock screen background in Windows using policy settings, including Intune, CSP, and GPO.
ms.topic: how-to
ms.date: 03/03/2025
author: paolomatarazzo
ms.author: paoloma
appliesto:
zone_pivot_groups: windows-versions-11-10
---

# Configure the desktop and lock screen backgrounds

Configuring desktop and lock screen backgrounds in Windows offers a simple yet effective way to enhance productivity, enforce consistency, and strengthen organizational branding.

Predefined backgrounds can display company logos, mission statements, or school emblems, reinforcing identity across devices. Examples where predefined backgrounds are especially valuable include kiosks, where lock screens can provide clear instructions, or student devices, where consistent branding fosters a sense of belonging and professionalism.

::: zone pivot="windows-11"

:::image type="content" source="images/contoso-lockscreen-11.png" alt-text="Screenshot of the Windows 11 lock screen with Windows spotlight enabled over an organization wallpaper." border="false":::

::: zone-end

::: zone pivot="windows-10"

:::image type="content" source="images/contoso-lockscreen-10.png" alt-text="Screenshot of the Windows 10 lock screen with Windows spotlight enabled over an organization wallpaper." border="false":::

::: zone-end

This article explains how to configure the desktop and lock screen backgrounds in Windows using policy settings. It includes examples of how to implement these configurations using Microsoft Intune, Configuration Service Provider (CSP), and Group Policy Object (GPO).

## Image ratios and scaling

A key consideration when using custom images is how they appear on devices with varying screen sizes and resolutions. For example, a custom image created in a 16:9 aspect ratio (such as 1600x900) scales properly on devices with 16:9 resolutions, like 1280x720 or 1920x1080. On devices with other aspect ratios, such as 4:3 (1024x768) or 16:10 (1280x800), the image's height scales correctly, but the width is cropped to match the aspect ratio. The image remains centered on the screen.

Images created in nonstandard aspect ratios might scale and center unpredictably when displayed on devices with different resolutions. To ensure consistent results, especially for images containing text (for example, legal statements), design the image in a 16:9 resolution and keep critical text within the 4:3 region. This approach ensures that the text remains visible across all aspect ratios.

## Configure the desktop background

**Windows edition requirements**. The following table summarizes the Windows editions and licensing requirements for configuring the desktop background:

| Windows edition | Intune/CSP | GPO |
|:-|:-:|:-:|
|Pro / Pro Education|✅|✅|
|Enterprise / Education|✅|✅|
|IoT Enterprise|✅|✅|

[!INCLUDE [tab-intro](../../../includes/configure/tab-intro.md)]

#### [:::image type="icon" source="../images/icons/intune.svg" border="false"::: **Intune/CSP**](#tab/intune)

[!INCLUDE [intune-settings-catalog-1](../../../includes/configure/intune-settings-catalog-1.md)]

| Category | Setting name | Value |
|--|--|--|
| **Personalization** | Desktop Image Url | An http or https URL to a jpg, jpeg, or png image file. |

[!INCLUDE [intune-settings-catalog-2](../../../includes/configure/intune-settings-catalog-2.md)]

Alternatively, you can configure devices using a [custom policy][INT-1] with the [Personalization CSP][CSP-1].

| Setting |
|--------|
| - **OMA-URI:** `./Vendor/MSFT/Personalization/DesktopImageUrl`<br>- **Data type:** string <br>- **Value:** An http or https URL to a jpg, jpeg, or png image file. |

#### [:::image type="icon" source="../images/icons/group-policy.svg" border="false"::: **GPO**](#tab/gpo)

[!INCLUDE [gpo-settings-1](../../../includes/configure/gpo-settings-1.md)]

| Group policy path | Group policy setting | Value |
| - | - | - |
| **User Configuration\Administrative Templates\Desktop\Desktop** |Desktop Wallpaper | Fully qualified path and name of the image file. You can use a local path or a UNC path. |

[!INCLUDE [gpo-settings-2](../../../includes/configure/gpo-settings-2.md)]

---

## Configure the lock screen background

**Windows edition requirements**. The following table summarizes the Windows editions and licensing requirements for configuring the lock screen background:

| Windows edition | Intune/CSP | GPO |
|:-|:-:|:-:|
|Pro / Pro Education|✅|❌|
|Enterprise / Education|✅|✅|
|IoT Enterprise|✅|✅|

[!INCLUDE [tab-intro](../../../includes/configure/tab-intro.md)]

#### [:::image type="icon" source="../images/icons/intune.svg" border="false"::: **Intune/CSP**](#tab/intune)

[!INCLUDE [intune-settings-catalog-1](../../../includes/configure/intune-settings-catalog-1.md)]

| Category | Setting name | Value |
|--|--|--|
| **Personalization** | Lock Screen Image Url| An http or https URL to a jpg, jpeg, or png image file. |

[!INCLUDE [intune-settings-catalog-2](../../../includes/configure/intune-settings-catalog-2.md)]

Alternatively, you can configure devices using a [custom policy][INT-1] with the [Personalization CSP][CSP-1].

| Setting |
|--------|
| - **OMA-URI:** `./Vendor/MSFT/Personalization/LockScreenImageUrl`<br>- **Data type:** string <br>- **Value:** An http or https URL to a jpg, jpeg, or png image file.|

#### [:::image type="icon" source="../images/icons/group-policy.svg" border="false"::: **GPO**](#tab/gpo)

[!INCLUDE [gpo-settings-1](../../../includes/configure/gpo-settings-1.md)]

| Group policy path | Group policy setting | Value |
| - | - | - |
| **Computer Configuration\Administrative Templates\Control Panel\Personalization** | Force a specific default lock screen and logon image | Fully qualified path and name of the image file. You can use a local path or a UNC path.|

[!INCLUDE [gpo-settings-2](../../../includes/configure/gpo-settings-2.md)]

---

> [!TIP]
> You can also configure a custom lock screen image using [organizational messages in the Microsoft 365 admin center][M365-1].

## User experience

When the policy is applied, the lock screen and desktop background images are set to the specified URL or path. The images are downloaded and cached locally on the device. The images are displayed in the background when the user signs in, and on the lock screen when the user locks the device.

## Windows spotlight

Windows spotlight is a feature that can display a different image on the lock screen and desktop background every day. Windows spotlight can also provide personalized content, such as tips and tricks for using Windows. You can configure a custom background image or lock screen image and still use Windows spotlight. When you do so, users can still receive suggestions, fun facts, tips, or organizational messages, but the background image is replaced with the custom image.

To learn more, see [Configure Windows spotlight](../windows-spotlight/index.md).

<!--links-->

[CSP-1]: /windows/client-management/mdm/personalization-csp
[M365-1]: /microsoft-365/admin/misc/organizational-messages-microsoft-365?view=o365-worldwide
[INT-1]: /mem/intune/configuration/settings-catalog
