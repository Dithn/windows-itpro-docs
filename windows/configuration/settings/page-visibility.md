---
title: Configure the Settings Page Visibility in Windows
description: Learn how to configure the pages listed in the Windows Settings app.
ms.topic: how-to
ms.date: 03/03/2025
author: paolomatarazzo
ms.author: paoloma
---

# Configure the Settings page visibility

*Settings* is a Windows application that offers a unified interface to manage the system settings. In certain scenarios, you might want to restrict access to specific Settings pages to ensure a more controlled and secure environment. This is especially beneficial for devices used in specific environments, such as kiosks or student devices, where limiting access to certain options can prevent unauthorized changes and maintain a consistent user experience.

:::image type="content" source="images/settings-page-visibility.png" alt-text="Screenshot of the Settings app configured with a policy setting to limit the categories displayed." border="false":::

This article explains how to configure the Settings app and how to implement the configurations using Microsoft Intune, Configuration Service Provider (CSP), and Group Policy Object (GPO).

## Page visibility list policy setting

You can configure the visibility of Settings pages using the *page visibility list* policy setting. This policy allows you to block a given set of pages from the Settings app. Blocked pages aren't visible in the app and can't be accessed through direct navigation via Uniform Resource Identifier (URI), context menu in Explorer, or other means. Direct navigation to a blocked page results in the first page of Settings displayed instead.

The page visibility list policy has two modes:

- **Show Specific Pages**
  - Start the policy string with `showonly:`
  - Follow it with a list of Settings page identifiers, separated by semicolons
- **Hide Specific Pages**
  - Start the policy string with `hide:`
  - Follow it with a list of Settings page identifiers, separated by semicolons

> [!NOTE]
> The identifier for any Settings page is the published URI for that page, minus the `ms-settings:` protocol part. For the list of categories and page identifiers, see [ms-settings: URI scheme reference](https://go.microsoft.com/fwlink/?linkid=2102995#ms-settings-uri-scheme-reference).

## Examples

Show only the **About** and **Bluetooth** pages. Their respective URIs are `ms-settings:about` and `ms-settings:bluetooth`:

`showonly:about;bluetooth`

Hide only the Bluetooth page, which has the URI `ms-settings:bluetooth`:

`hide:bluetooth`

## Configuration

[!INCLUDE [tab-intro](../../../includes/configure/tab-intro.md)]

#### [:::image type="icon" source="../images/icons/intune.svg" border="false"::: **Intune**](#tab/intune)

[!INCLUDE [intune-settings-catalog-1](../../../includes/configure/intune-settings-catalog-1.md)]

| Category | Setting name | Value |
|--|--|--|
| **Settings** | - Page Visibility List<br>- Page Visibility List (User)| List of URIs to show or hide, separated by semicolons.|

[!INCLUDE [intune-settings-catalog-2](../../../includes/configure/intune-settings-catalog-2.md)]

#### [:::image type="icon" source="../images/icons/csp.svg"::: **CSP**](#tab/csp)

You can configure devices using the [Policy CSP][CSP-1].

| Setting |
|--|
|- **OMA-URI:** `./Device/Vendor/MSFT/Policy/Config/Settings/PageVisibilityList`<br>- **Data type:** string<br>- **Value:** List of URIs to show or hide, separated by semicolons.<br><br>Or<br><br>- **OMA-URI:** `./User/Vendor/MSFT/Policy/Config/Settings/PageVisibilityList`<br>- **Data type:** string<br>- **Value:** List of URIs to show or hide, separated by semicolons.|

#### [:::image type="icon" source="../images/icons/group-policy.svg" border="false"::: **GPO**](#tab/gpo)

[!INCLUDE [gpo-settings-1](../../../includes/configure/gpo-settings-1.md)]

| Group policy path | Group policy setting | Value |
| - | - | - |
| **Computer Configuration\Administrative Templates\Control Panel**<br><br>Or<br><br>**User Configuration\Administrative Templates\Control Panel** | Settings Page Visibility | List of URIs to show or hide, separated by semicolons.|

[!INCLUDE [gpo-settings-2](../../../includes/configure/gpo-settings-2.md)]

---

## User Experience

By controlling the visibility of Settings pages, you can create a customized user experience tailored to your organization's specific needs. Once the policy is applied, users have access only to the Settings pages you explicitly allow, ensuring a focused and streamlined interface.

<!--links-->

[CSP-1]: /windows/client-management/mdm/policy-csp-settings#pagevisibilitylist
[M365-1]: /microsoft-365/admin/misc/organizational-messages-microsoft-365?view=o365-worldwide
[INT-1]: /mem/intune/configuration/settings-catalog
