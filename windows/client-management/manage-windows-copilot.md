---
title: Updated Windows and Microsoft 365 Copilot Chat experience
description: Learn about changes to the Copilot in Windows experience for commercial environments and how to configure it for your organization.
ms.topic: overview
ms.subservice: windows-copilot
ms.date: 06/09/2025
ms.author: mstewart
author: mestew
ms.collection:
  - windows-copilot
  - magic-ai-copilot
appliesto:
- ✅ <a href="https://learn.microsoft.com/windows/release-health/supported-versions-windows-client" target="_blank">Windows 11, version 22H2 or later</a>
---

# Updated Windows and Microsoft 365 Copilot Chat experience
<!--8445848, 9294806-->

>**Looking for consumer information?** See [Getting started with Copilot on Windows](https://support.microsoft.com/topic/1159c61f-86c3-4755-bf83-7fbff7e0982d). **Looking for more information on Microsoft 365 Copilot Chat experiences?** See [Understanding the different Microsoft 365 Copilot Chat experiences](https://support.microsoft.com/topic/cfff4791-694a-4d90-9c9c-1eb3fb28e842).

## Enhanced data protection with enterprise data protection

Starting in September 2024, the Copilot experience on Windows is changing to enhance data security, privacy, compliance, and simplify the user experience, for users signed in with a Microsoft Entra work or school account. [Microsoft 365 Copilot Chat](https://techcommunity.microsoft.com/t5/copilot-for-microsoft-365/updates-to-microsoft-copilot-to-bring-enterprise-data-protection/ba-p/4217152) is available at no additional cost and it redirects users to a new simplified interface designed for work and education. [Enterprise data protection (EDP)](/copilot/microsoft-365/enterprise-data-protection) refers to controls and commitments, under the Data Protection Addendum and Product Terms, that apply to customer data for users of Microsoft 365 Copilot and Microsoft 365 Copilot Chat. This means that security, privacy, compliance controls and commitments available for Microsoft 365 Copilot will extend to Microsoft 365 Copilot Chat prompts and responses. Prompts and responses are protected by the same terms and commitments that are widely trusted by our customers. This is an improvement on top of the previous commercial data protection (CDP) promise. For more information, see the [Microsoft 365 Copilot Chat updates and enterprise data protection FAQ](/copilot/edpfaq).


## Users signing in to new PCs with Microsoft Entra accounts

For users signing in to new PCs with work or school accounts, the following experience occurs:

-	The Microsoft 365 Copilot app is pinned to the taskbar - this is the app that typically comes preinstalled with Windows and includes convenient access to Office apps such as Word, PowerPoint, etc. 
-	Users that have the Microsoft 365 Copilot license have Microsoft 365 Copilot Chat pinned by default inside the Microsoft 365 Copilot app. 
-	Within the Microsoft 365 Copilot app, the Microsoft 365 Copilot Chat icon is situated next to the home button.
    - Microsoft 365 Copilot Chat (`web` grounding chat) isn't the same as Microsoft 365 Copilot (`web` and `work` scope), which is a separate add-on license. 
    - Microsoft 365 Copilot Chat is available at no additional cost to customers with a Microsoft Entra account. Microsoft 365 Copilot Chat is the entry point for Copilot at work. While the Copilot chat experience helps users ground their conversations in web data, Microsoft 365 Copilot allows users to incorporate both web and work data they have access to into their conversations by switching between work and web modes in Business Chat. 
   - For users with the Microsoft 365 Copilot license, they can toggle between the web grounding-based chat capabilities of Microsoft 365 Copilot Chat and the work scoped chat capabilities of Microsoft 365 Copilot. 
-	Customers that don't have a license for Microsoft 365 Copilot are asked if they want to pin Microsoft 365 Copilot Chat to ensure they have easy access to Copilot. To set the default behavior, admins should [set pinning options](/copilot/microsoft-365/pin-copilot) in the Microsoft 365 admin center. 
-	If admins elect not to pin Copilot and indicate that users can be asked, users will be asked to pin it themselves in the Microsoft 365 Copilot app, Outlook, and Teams. 
-	If admins elect not to pin Microsoft 365 Copilot Chat and indicate that users can't be asked, Microsoft 365 Copilot Chat won't be available via the Microsoft 365 Copilot app, Outlook, or Teams. Users have access to Microsoft 365 Copilot Chat from [https://www.microsoft.com/copilot](https://www.microsoft.com/copilot) unless that URL is blocked by the IT admin.
-	If the admins make no selection, users will be asked to pin Microsoft 365 Copilot Chat by themselves for easy access. 

IT admins can pin the Microsoft 365 Copilot app to the Windows taskbar to enable easy and seamless access for users. This can be managed using policies  to [configure applications pinned to the Windows taskbar](/windows/configuration/taskbar/pinned-apps).

## When will this happen?

The update to Microsoft 365 Copilot Chat to offer enterprise data protection roll out started in September 2024. Changes were rolled out to managed PCs starting with the September 2024 optional nonsecurity preview release, and then the October 2024 monthly security update for all supported versions of Windows 11. These changes were applied to Windows 10 PCs in November 2024. This update replaced the legacy Copilot in Windows experience.
 
The Copilot app is automatically enabled after you install the Windows updates listed above if you haven't previously enabled a group policy to prevent the installation of Copilot. The [AppLocker policy](/windows/security/application-security/application-control/app-control-for-business/applocker/applocker-overview) is available to control this Copilot experience before installing these Windows updates mentioned above or any subsequent Windows updates. 
 
Note that the Copilot app, which is a consumer experience, doesn't support Microsoft Entra authentication and users trying to sign in to the app using a Microsoft Entra account will be redirected to https://copilot.cloud.microsoft/ in their default browser. For users authenticating with a Microsoft Entra account, they should access Copilot through the Microsoft 365 Copilot app as the entry point. We recommend you pin Copilot to the navigation bar of the Microsoft 365 Copilot app to enable easy access.


## Remove or prevent installation of the Copilot app

You can remove or uninstall the Copilot app from your device by using one of the following methods:

1. Enterprise users can uninstall the [Copilot app](https://apps.microsoft.com/detail/9NHT9RB2F4HD), which is a consumer experience, by going to **Settings** > **Apps** >**Installed Apps**. Select the three dots appearing on the right side of the app and select **Uninstall** from the dropdown list.

1. If you are an IT administrator, you can prevent installation of the app or remove the Copilot app using one of the following methods:
   1. Prevent installation of the Copilot app:
     - Configure [AppLocker policy](/windows/security/application-security/application-control/app-control-for-business/applocker/applocker-overview) before installing Windows update. AppLocker helps you control which apps and files users can run. Note: AppLocker policy should be used instead of the [Turn Off Windows Copilot](mdm/policy-csp-windowsai.md#turnoffwindowscopilot) legacy policy setting and its MDM equivalent, [TurnOffWindowsCopilot](mdm/policy-csp-windowsai.md#turnoffwindowscopilot). The policy is subject to near-term deprecation. 
     - The Applocker policy can be configured by following one of the methods listed in [Edit an AppLocker policy](/windows/security/application-security/application-control/app-control-for-business/applocker/edit-an-applocker-policy) and adding the below text to the policy:
     </br>**Publisher**: CN=MICROSOFT CORPORATION, O=MICROSOFT CORPORATION, L=REDMOND, S=WASHINGTON, C=US
     </br> **Package name**: MICROSOFT.COPILOT
    </br> **Package version**: * (and above)

   1. Remove the Copilot app using PowerShell script:
      1. Open a Windows PowerShell window. You can do this by opening the Start menu, typing `PowerShell`, and selecting **Windows PowerShell** from the results.
      1. Once the PowerShell window is open, enter the following commands:
       ```powershell
       # Get the package full name of the Copilot app
       $packageFullName = Get-AppxPackage -Name "Microsoft.Copilot" | Select-Object -ExpandProperty PackageFullName
       # Remove the Copilot app
       Remove-AppxPackage -Package $packageFullName
       ```


## Implications for the Copilot hardware key
<!--9598546, 10050561-->
The updated Copilot hardware key experience on Windows 11 devices offers a more streamlined and context-aware interaction model for both consumer and commercial users. For commercial customers, pressing the Copilot key now opens a lightweight prompt box for quick access to Microsoft 365 Copilot, allowing users to stay in their workflow without switching apps or screens. This prompt can be expanded into the full Microsoft 365 Copilot app for more functionality. This change started rolling out in the May 2025 optional nonsecurity preview release. It addressed feedback from enterprise users who found the key defaulted to a consumer experience on managed devices. IT admins can configure or remap the key using [group policy or CSP settings](#policies-to-manage-the-copilot-key) to meet organizational needs. 

If you're a software developer, you'll need to register your app as a [Microsoft Copilot hardware key provider](/windows/apps/develop/windows-integration/microsoft-copliot-key-provider) to allow users to remap the Copilot key to your app. This is done by adding `com.microsoft.windows.copilotkeyprovider` as the **Name** within the [uap3:AppExtension](/uwp/schemas/appxpackage/uapmanifestschema/element-uap3-appextension-manual) for your app's package manifest file.


## Policies to manage the Copilot key

Policies are available so admins can configure the target app of the Copilot hardware key. For more information, see [WindowsAI Policy CSP](mdm/policy-csp-windowsai.md). 

To configure the Copilot key, use the following policy:

| &nbsp; | Setting  |
|---|---|
| **CSP** | ./User/Vendor/MSFT/Policy/Config/WindowsAI/[SetCopilotHardwareKey](mdm/policy-csp-windowsai.md#setcopilothardwarekey) |
| **Group policy** | User Configuration > Administrative Templates > Windows Components > Windows Copilot > **Set Copilot Hardware Key** |



## End user settings for the Copilot key

If you choose to provide users in your organization with the choice to manage their own experience, a protocol to launch the **Settings** app remap the Copilot key is available. The following can be used by apps and scripts to bring the user to the setting so they can modify it to meet their needs:

`ms-settings:personalization-textinput-copilot-hardwarekey`

:::image type="content" border="true" source="./images/9598546-copilot-key-settings.png" alt-text="Screenshot of the text input page in Settings." lightbox="./images/9598546-copilot-key-settings.png":::


If a user signed in with their Microsoft Entra account doesn't already have the key mapped to the Microsoft 365 Copilot app, they can select the app by going to **Settings** > **Personalization** > **Text input**, then selecting from the dropdown menu in the setting called **Customize Copilot key on keyboard**. This dropdown has options for: **Search**, **Custom**, or a currently mapped app if one is selected.

To map the key to the Microsoft 365 Copilot app, the user should select **Custom** and then choose the Microsoft 365 Copilot app from the app picker. If this app picker is empty or doesn't include the Microsoft 365 Copilot app, they should reinstall it from the Microsoft Store. 

Users can also choose to have the Copilot key launch an app that is MSIX packaged and signed, ensuring the app configured to the Copilot key can remap to meet security and privacy requirements. If the app isn't listed in the app picker for the Copilot key, it's possible that the app provider hasn't registered it yet in their package manifest file as a [Microsoft Copilot hardware key provider](/windows/apps/develop/windows-integration/microsoft-copliot-key-provider). Check with your app provider to see if they've recently updated the app and that you have the lastest version of their app installed.


## Copilot installation with Windows updates and controls

If you're an IT administrator, you can remove the consumer Copilot app by following one of the steps in the [Remove or prevent installation of the Copilot app](#remove-or-prevent-installation-of-the-copilot-app) section or configure the [AppLocker policy](/windows/security/application-security/application-control/app-control-for-business/applocker/applocker-overview) before installing Windows updates. When the AppLocker policy for Copilot is enabled, it will:

- Prevent the consumer app from being installed if it isn't already on the device.
- Block the consumer app from being launched if it's already installed.