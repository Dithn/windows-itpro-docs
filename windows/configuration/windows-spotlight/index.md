---
title: Configure Windows spotlight
description: Learn how to configure Windows spotlight using Group Policy and mobile device management (MDM) settings.
ms.topic: how-to
ms.date: 12/05/2024
ms.author: paoloma
author: paolomatarazzo
appliesto:
zone_pivot_groups: windows-versions-11-10
---

# Configure Windows spotlight

Windows spotlight is a feature that displays different wallpapers and offers suggestions, fun facts, tips, or organizational messages:

::: zone pivot="windows-11"

- **Wallpapers**: Windows spotlight displays a new image on the lock screen and in the background every day
- **Suggestions, fun facts, tips**: recommendations on how to enhance the user's productivity of Microsoft products. They're displayed in different locations, such as the lock screen, the background, the taskbar, or the Get Started app
- **Organizational messages**: messages from your organization, which can be displayed in the lock screen, taskbar, the notification area, or the Get Started app

:::image type="content" source="images/lockscreen-11.png" alt-text="Screenshot of the Windows 11 lock screen with Windows Spotlight enabled." border="false":::

> [!NOTE]
> After installing the [KB5046633 (October 22, 2024)](https://support.microsoft.com/topic/22631-4460-6ff7b117-cd80-471a-a9ac-48a794bda2d6), the default Windows wallpaper changes to Windows spotlight. To modify this behavior, use the [AllowSpotlightCollection policy setting](#policy-settings), or configure a custom lock screen and background image.

::: zone-end

::: zone pivot="windows-10"

- **Wallpapers**: Windows spotlight displays a new image on the lock screen every day
- **Suggestions, fun facts, tips**: recommendations on how to enhance the user's productivity of Microsoft products. They're displayed in different locations, such as the lock screen, the background, the taskbar, or the Get Started app
- **Organizational messages**: messages from your organization, which can be displayed in the lock screen, taskbar, the notification area, or the Get Started app

:::image type="content" source="images/lockscreen-10.png" alt-text="Screenshot of the Windows 10 lock screen with Windows Spotlight enabled." border="false":::

> [!NOTE]
> After installing the [KB5048652 (December 10, 2024)](https://support.microsoft.com/topic/19045-5247-454fbd4c-0723-449e-915b-8515ab41f8e3), the default Windows wallpaper changes to Windows spotlight. To modify this behavior, configure a custom lock screen and background image.

::: zone-end

## Windows edition and licensing requirements

Windows spotlight is available on Windows Enterprise and Education editions only.

## Configuration options

Windows spotlight is enabled by default, but you can customize it to meet your organization's needs. There are several options to configure Windows spotlight.

If you need to configure a device for a single user, go to:

::: zone pivot="windows-11"

- **Settings** > **Personalization** > **[Background](ms-settings:personalization-background)**. To change the background image to Windows spotlight, select **Windows spotlight** from the **Personalize your background** drop-down menu

::: zone-end

- **Settings** > **Personalization** > **[Lock screen](ms-settings:personalization-lockscreen)**. To change the lock screen image to Windows spotlight, select **Windows spotlight** from the **Personalize your lock screen** drop-down menu

For advanced customizations and when you need to configure multiple devices, you can use one of the following options:

- Configuration Service Provider (CSP): commonly used for devices managed by a Mobile Device Management (MDM) solution, like Microsoft Intune. CSPs can also be configured with [provisioning packages](../provisioning-packages/how-it-pros-can-use-configuration-service-providers.md#csps-in-windows-configuration-designer), which are used at deployment time or for unmanaged devices. To configure Windows spotlight, use the [Experience Policy CSP][CSP-1]
- Group policy (GPO): used for devices that are Active Directory joined or Microsoft Entra hybrid joined, and not managed by a device management solution. Group policy can also be used for devices that aren't joined to an Active Directory domain, using the local group policy editor

## Policy settings

Here's a sorted list of the policy settings to configure Windows spotlight:

::: zone pivot="windows-11"
|Policy name| CSP | GPO |
|-|-|-|
|[AllowSpotlightCollection](/windows/client-management/mdm/policy-csp-experience#allowspotlightcollection)|✅|❌|
|[AllowThirdPartySuggestionsInWindowsSpotlight](/windows/client-management/mdm/policy-csp-experience#allowthirdpartysuggestionsinwindowsspotlight)|✅|✅|
|[AllowWindowsSpotlight](/windows/client-management/mdm/policy-csp-experience#allowwindowsspotlight)|✅|✅|
|[AllowWindowsSpotlightOnActionCenter](/windows/client-management/mdm/policy-csp-experience#allowwindowsspotlightonactioncenter)|✅|✅|
|[AllowWindowsSpotlightOnSettings](/windows/client-management/mdm/policy-csp-experience#allowwindowsspotlightonsettings)|✅|✅|
|[AllowWindowsSpotlightWindowsWelcomeExperience](/windows/client-management/mdm/policy-csp-experience#allowwindowsspotlightwindowswelcomeexperience)|✅|✅|
|[ConfigureWindowsSpotlightOnLockScreen](/windows/client-management/mdm/policy-csp-experience#configurewindowsspotlightonlockscreen)|✅|✅|

::: zone-end

::: zone pivot="windows-10"

|Policy name| CSP | GPO |
|-|-|-|
|[AllowThirdPartySuggestionsInWindowsSpotlight](/windows/client-management/mdm/policy-csp-experience#allowthirdpartysuggestionsinwindowsspotlight)|✅|✅|
|[AllowWindowsSpotlight](/windows/client-management/mdm/policy-csp-experience#allowwindowsspotlight)|✅|✅|
|[AllowWindowsSpotlightOnActionCenter](/windows/client-management/mdm/policy-csp-experience#allowwindowsspotlightonactioncenter)|✅|✅|
|[AllowWindowsSpotlightOnSettings](/windows/client-management/mdm/policy-csp-experience#allowwindowsspotlightonsettings)|✅|✅|
|[AllowWindowsSpotlightWindowsWelcomeExperience](/windows/client-management/mdm/policy-csp-experience#allowwindowsspotlightwindowswelcomeexperience)|✅|✅|
|[ConfigureWindowsSpotlightOnLockScreen](/windows/client-management/mdm/policy-csp-experience#configurewindowsspotlightonlockscreen)|✅|✅|

::: zone-end

## Custom lock screen and background images

You can replace the Windows spotlight lock screen and background images with a custom image. When you do so, users can still receive suggestions, fun facts, tips, or organizational messages, but the background image is replaced with the custom image.

To learn more, see [Configure the desktop and lock screen background](../background/index.md).

## User experience

When Windows spotlight is enabled, devices apply a new image on the lock screen and in the background every day. The image is displayed in the background when the user signs in, and on the lock screen when the user locks the device. Users can still receive suggestions, fun facts, tips, or organizational messages. If you deploy a custom lock screen or background image, devices apply the custom image instead of the Windows spotlight image:

::: zone pivot="windows-11"

:::image type="content" source="images/contoso-lockscreen-11.png" alt-text="Screenshot of the Windows 11 lock screen with Windows spotlight enabled over an organization wallpaper." border="false":::

::: zone-end

::: zone pivot="windows-10"

:::image type="content" source="images/contoso-lockscreen-10.png" alt-text="Screenshot of the Windows 10 lock screen with Windows spotlight enabled over an organization wallpaper." border="false":::

::: zone-end

## Next steps

To learn more about organizational messages, see:

- [Organizational messages in the Microsoft 365 admin center][M365-1]
- [Organizational messages in Microsoft Intune][INT-1]

<!--links-->

[CSP-1]: /windows/client-management/mdm/policy-csp-experience
[INT-1]: /mem/intune/remote-actions/organizational-messages-overview
[M365-1]: /microsoft-365/admin/misc/organizational-messages-microsoft-365?view=o365-worldwide
