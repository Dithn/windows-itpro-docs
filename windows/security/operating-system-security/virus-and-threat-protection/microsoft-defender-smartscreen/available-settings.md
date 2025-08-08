---
title: Available Microsoft Defender SmartScreen settings
description: A list of all available settings for Microsoft Defender SmartScreen using Group Policy and mobile device management (MDM) settings.
ms.date: 04/28/2025
ms.topic: reference
---

# Available Microsoft Defender SmartScreen settings

Microsoft Defender SmartScreen respects Intune, Group Policy, and mobile device management (MDM) settings. You can configure Microsoft Defender SmartScreen to block suspicious content entirely, or show users a warning but allow them to continue to load the content.

See [Windows settings to protect devices using Intune](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-smartscreen-settings) for the controls you can use in Intune.

## Group Policy settings

SmartScreen uses registry-based Administrative Template policy settings.

|Setting|Description|
|---|--- |
|Administrative Templates > Windows Components > Windows Defender SmartScreen > Explorer > Configure Windows Defender SmartScreen | This policy setting controls Microsoft Defender SmartScreen's Application Reputation ("Check apps and files") feature.<br/><br/>If you enable this setting, it turns on Microsoft Defender SmartScreen and your users are unable to turn it off. When enabling this feature, you must pick whether users may choose to ignore warnings and run an unknown or malicious program.<br/><br/>If you disable this setting, it turns off Microsoft Defender SmartScreen and your users are unable to turn it on.<br/><br/>If you don't configure this setting, your users can decide whether to use Microsoft Defender SmartScreen's Application Reputation feature.|
|Administrative Templates > Windows Components > Windows Defender SmartScreen > Explorer > Configure App Install Control| This policy setting allows you to control whether users can install downloaded apps from outside of the Microsoft Store.<br/><br/>This setting does not impact opening files from USB devices, local network shares, or other non-internet sources.|
|Administrative Templates > Microsoft Edge > SmartScreen settings > Configure Microsoft Defender SmartScreen | This policy setting lets you configure Microsoft Defender SmartScreen in the Microsoft Edge web browser. Microsoft Defender SmartScreen provides warning messages to help protect your users from potential phishing sites, tech scams, and malicious software. By default, Microsoft Defender SmartScreen is turned on.<br><br>If you enable this setting, Microsoft Defender SmartScreen is turned on, and users can't turn it off.<br><br>If you disable this setting, Microsoft Defender SmartScreen is turned off, and users can't turn it on. <br><br>If you don't configure this setting, users can choose whether to use Microsoft Defender SmartScreen.|
|Administrative Templates > Microsoft Edge > SmartScreen settings > Prevent bypassing Windows Defender SmartScreen prompts for sites | This policy setting lets you decide whether users can override  Microsoft Defender SmartScreen warnings about potentially malicious websites.<br><br>If you enable this setting, users can't ignore Microsoft Defender SmartScreen warnings and will be blocked from continuing to suspicious sites. <br><br>If you disable or don't configure this setting, users can ignore Microsoft Defender SmartScreen warnings and continue to suspicious sites. |
|Administrative Templates > Microsoft Edge > SmartScreen settings > Prevent bypassing of Microsoft Defender SmartScreen warnings about downloads | This policy setting lets you decide whether users can override Microsoft Defender SmartScreen warnings about unverified (potentially malicious) downloads.<br><br>If you enable this setting, users can't ignore Microsoft Defender SmartScreen warnings and will be blocked from downloading unverified files. <br><br>If you disable or don't configure this setting, users can ignore Microsoft Defender SmartScreen warnings and download unverified files. |

> [!NOTE]
> To install the Administrative Templates ADMX file for Microsoft Edge browser policies, see [Configure Microsoft Edge](/deployedge/configure-microsoft-edge).

## MDM settings

If you manage your policies using Microsoft Intune, use these MDM policy settings. All settings support desktop computers running Windows 10/11 Pro or Windows 10/11 Enterprise, enrolled with Microsoft Intune.

- [AllowSmartScreen](/windows/client-management/mdm/policy-csp-browser#allowsmartscreen)
- [EnableAppInstallControl](/windows/client-management/mdm/policy-csp-smartscreen#enableappinstallcontrol)
- [EnableSmartScreenInShell](/windows/client-management/mdm/policy-csp-smartscreen#enablesmartscreeninshell)
- [PreventOverrideForFilesInShell](/windows/client-management/mdm/policy-csp-smartscreen#preventoverrideforfilesinshell)
- [PreventSmartScreenPromptOverride](/windows/client-management/mdm/policy-csp-browser#preventsmartscreenpromptoverride)
- [PreventSmartScreenPromptOverrideForFiles](/windows/client-management/mdm/policy-csp-browser#preventsmartscreenpromptoverrideforfiles)

## Recommended Group Policy and MDM settings for your organization

By default, Microsoft Defender SmartScreen allows users to bypass warnings, which allows users to continue to an unsafe site or run an unsafe file, even after being warned. Because of this possibility, we strongly recommend that you set up Microsoft Defender SmartScreen to block high-risk interactions instead of providing just a warning.

To better help you protect your organization, we recommend turning on and using these specific Microsoft Defender SmartScreen Group Policy and MDM settings.

| Group Policy setting | Recommendation |
|--|--|
| Administrative Templates > Windows Components > Explorer > Configure Windows Defender SmartScreen | **Enable with the Warn and prevent bypass option.**  Stops users from ignoring warning messages about malicious files downloaded from the Internet. |
| Administrative Templates > Microsoft Edge > SmartScreen settings > Configure Microsoft Defender SmartScreen | **Enable.**  Turns on Microsoft Defender SmartScreen. |
| Administrative Templates > Microsoft Edge > Prevent bypassing Windows Defender SmartScreen prompts for sites | **Enable.**  Stops users from ignoring warning messages and continuing to a potentially malicious website. |
|Administrative Templates > Microsoft Edge > Prevent bypassing of Microsoft Defender SmartScreen warnings about downloads  |**Enable.**  Stops users from ignoring warning messages and downloading an unverified file |

| MDM setting | Recommendation |
|--|--|
| Browser/AllowSmartScreen | **1.**  Turns on Microsoft Defender SmartScreen. |
| Browser/PreventSmartScreenPromptOverride | **1.**  Stops users from ignoring warning messages and continuing to a potentially malicious website. |
| Browser/PreventSmartScreenPromptOverrideForFiles | **1.**  Stops users from ignoring warning messages and continuing to download potentially malicious files. |
| SmartScreen/EnableSmartScreenInShell | **1.**  Turns on Microsoft Defender SmartScreen in Windows.<br/><br/>Requires at least Windows 10, version 1703. |
| SmartScreen/PreventOverrideForFilesInShell | **1.**  Stops users from ignoring warning messages about malicious files downloaded from the Internet.<br/><br/>Requires at least Windows 10, version 1703. |

> [!NOTE]
> For a list of settings available for Enhanced phishing protection, see [Enhanced phishing protection](enhanced-phishing-protection.md#configure-enhanced-phishing-protection-for-your-organization).
