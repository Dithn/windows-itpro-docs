---
title: Manage AI features in Notepad
description: Learn how to manage AI features in Notepad using Microsoft Intune and Group Policy.
ms.topic: how-to
ms.subservice: windows-copilot
ms.date: 04/30/2025
ms.author: vinpa
author: vinaypamnani-msft
appliesto:
- ✅ <a href="https://learn.microsoft.com/windows/release-health/supported-versions-windows-client\" target="_blank">Windows 11</a>
---

# Manage AI features in Notepad

> **Looking for consumer information?** See [Enhance Your Writing with AI in Notepad](https://support.microsoft.com/topic/4088b954-c97b-46dc-813f-959be01746d5).

Notepad in Windows includes AI features powered by Copilot that help refine and shorten text with the assistance of GPT. By default, these AI features are enabled on managed devices. IT admins can choose if they want to allow these features to be used in their organizations.

This article provides information about managing AI features for Notepad in a commercial environment.

## Download the Notepad administrative template (ADMX)

The [Notepad Administrative Template (ADMX)](https://download.microsoft.com/download/72ea16a9-4cc9-4032-945d-3a56a483d034/WindowsNotepadAdminTemplates.cab) can be downloaded from the Microsoft Download Center. The group policy settings contained in the ADMX file are machine-wide for all users.

## Policy settings

### DisableAIFeaturesInNotepad

This policy setting allows you to control whether AI features are disabled in the Windows Notepad app. 

- If this policy is enabled, users can't access AI features in the Notepad app.
- If this policy is disabled or not configured, users can access AI features in the Notepad app.

**Supported versions**

- Windows 11, version 22H2 or later.
- Notepad version 11.2503.16.0 or later.

## Configure policies

To configure Notepad policies, you can use:

- Microsoft Intune
- Group policy
- Registry

The following instructions provide details how to configure your devices. Select the option that best suits your needs.

#### [:::image type="icon" source="images/icons/intune.svg"::: **Intune**](#tab/intune)


To configure devices using Microsoft Intune, [import the Notepad administrative template (ADMX) files](/intune/intune-service/configuration/administrative-templates-import-custom#add-the-admx-and-adml-files) and then [create a custom **Configuration profile**](/intune/intune-service/configuration/administrative-templates-import-custom#create-a-profile-using-your-imported-files) based on the imported ADMX files. 

> [!NOTE]
> The Notepad administrative template (ADMX) depends on the Windows administrative template (`C:\Windows\PolicyDefinitions\Windows.admx`) file, so make sure you import it as well.

<!-- 
#### [:::image type="icon" source="images/icons/csp.svg"::: **CSP**](#tab/csp)
TODO 
-->

#### [:::image type="icon" source="images/icons/group-policy.svg" border="false"::: **GPO**](#tab/gpo)

For machines within a corporate network, you can use Group Policy with Active Directory (AD) to deploy Notepad policies. Steps:

1. Download the latest [Notepad administrative template (ADMX)](#download-the-notepad-administrative-template-admx).

2. On your domain controllers, copy and paste the following files to the relevant location, depending if you store Group Policy templates in the local `PolicyDefinitions` folder or the [Group Policy Central Store](/troubleshoot/windows-client/group-policy/create-and-manage-central-store). Replace `contoso.com` with your domain name, and `en-US` if you're using a different language.
   
   - **Filename**: `WindowsNotepad.admx`     
     - **Local location**: `C:\Windows\PolicyDefinitions\`
     - **Central Store**: `\\contoso.com\SYSVOL\contoso.com\Policies\PolicyDefinitions`
   
   - **Filename**: `en-US\WindowsNotepad.adml`     
     - **Local location**: `C:\Windows\PolicyDefinitions\en-US\`
     - **Central Store**: `\\contoso.com\SYSVOL\contoso.com\Policies\PolicyDefinitions\en-US`

3. On a device you use to manage Group Policy, open the **Group Policy Management Console (GPMC)** and create or edit a policy that targets your devices.

4. To verify that the Notepad administrative template is available, browse to **Computer Configuration** > **Policies** > **Administrative Templates** > **Windows Components** > **Notepad** . You should see policy settings for Notepad available for you to configure.

#### [:::image type="icon" source="images/icons/registry.svg" border="false"::: **Registry**](#tab/reg)

To disable AI features in Notepad, set the `DisableAIFeatures` registry value to `1` under `HKLM:\SOFTWARE\Policies\WindowsNotepad`.
