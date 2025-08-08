---
title: Configure the agent in Windows Settings
description: Learn how to configure the agent in Windows Settings.
ms.topic: how-to
ms.date: 05/05/2025
author: paolomatarazzo
ms.author: paoloma
appliesto:
- ✅ <a href=/windows/release-health/supported-versions-windows-client target=_blank>Windows 11</a>
---

# Configure the agent in Windows Settings

Starting in Windows 11, version 24H2 with [KB5062660][KB-1], the agent in Windows Settings is a feature that uses on-device AI to help you find and change settings on your PC. It can also help you troubleshoot issues by providing recommendations and automating tasks based on your input.

The agent guides users through finding and changing settings, offering relevant information and recommendations. With user permission, it can automate the process of changing settings. This feature enhances search within Windows Settings by enabling natural language queries and utilizing an AI model for intelligent search suggestions.

<!--The agent is designed to respect existing policy settings on the device, ensuring that it doesn't override any restrictions already in place.-->


## Requirements

The agent in Settings is currently available only on Windows 11 devices that meet the following criteria:

### System requirements

> [!div class="checklist"]
> - Windows 11, version 24H2 with [KB5062660][KB-1] and later
> - A [Copilot+ PC](https://aka.ms/copilotpluspcs)
> - Qualcomm Snapdragon. Intel and AMD support will be available at a later time
> - The device must have enabled the [temporary enterprise feature control](/windows/whats-new/temporary-enterprise-feature-control) policy setting

### Language and geography requirements

> [!div class="checklist"]
> - Language: English only
> - Geography: All countries, except Canada and China

## How it works

The agent in Settings uses a lightweight language model called *Settings Mu*, which is fine-tuned using Settings data to help users quickly find and adjust system settings.

- The model runs locally on the device, analyzing a user's query to match with relevant settings already available in Settings.
- If the model can't confidently classify a query to a specific setting, standard search results are displayed instead.
- The agent only suggests settings; it doesn't make any changes automatically. The user must explicitly request the agent to make a change.
- If needed, the user can easily *undo* the change.

The Settings Mu model has undergone fairness evaluations, and comprehensive Responsible AI, security, and privacy assessments. These steps ensure the technology is effective, equitable, and aligned with [Microsoft's Responsible AI principles][RAI].

## Configuration

As an administrator, you can enable or disable the agent in Settings using a policy setting:

- When the policy setting is enabled, the agent experience isn't available, and search results are limited to statically indexed searches and semantic searches.
- When the policy setting is disabled (default), the agent search experience is available. The agent can provide recommendations and automate tasks based on user input.

[!INCLUDE [tab-intro](../../../includes/configure/tab-intro.md)]

#### [:::image type="icon" source="../images/icons/intune.svg" border="false"::: **Intune**](#tab/intune)

[!INCLUDE [intune-settings-catalog-1](../../../includes/configure/intune-settings-catalog-1.md)]

| Category | Setting name |
|--|--|
| **Windows AI** | Disable Settings Agent |

[!INCLUDE [intune-settings-catalog-2](../../../includes/configure/intune-settings-catalog-2.md)]

#### [:::image type="icon" source="../images/icons/csp.svg"::: **CSP**](#tab/csp)

You can configure devices using the [Policy CSP][CSP-1].

| Setting |
|--|
|- **OMA-URI:** `./Vendor/MSFT/Policy/Config/WindowsAI/`[DisableSettingsAgent](/windows/client-management/mdm/policy-csp-windowsai)<br>- **Data type:** Integer<br>- **Value:** <br>&nbsp;&nbsp;&nbsp;&nbsp;- `0` (default): the agent search experience in Settings is enabled <br>&nbsp;&nbsp;&nbsp;&nbsp;- `1`: the agent search experience in Settings is disabled|

#### [:::image type="icon" source="../images/icons/group-policy.svg" border="false"::: **GPO**](#tab/gpo)

[!INCLUDE [gpo-settings-1](../../../includes/configure/gpo-settings-1.md)]

| Group policy path | Group policy setting |
| - | - |
| **Computer Configuration** > **Administrative Templates** > **Windows Components** > **Windows AI** | Disable Settings Agent |

[!INCLUDE [gpo-settings-2](../../../includes/configure/gpo-settings-2.md)]

---

## User experience

If the agent is enabled, users can access it by opening Settings and typing their question in the search box. The agent provides relevant information and recommendations based on the user's input.

:::image type="content" source="images/settings-agent.png" alt-text="Screenshot of Settings showing the search agent with an example search." border="false":::

## Microsoft's commitment to responsible AI and Privacy

Microsoft has been working to advance AI responsibly since 2017, when we first defined our AI principles and later operationalized our approach through our Responsible AI Standard. Privacy and security are core principles as we develop and deploy AI systems. We work to help our customers use our AI products responsibly, sharing our learnings, and building trust-based partnerships. For more information about our responsible AI efforts, the principles that guide us, and the tools and capabilities developed to ensure responsible AI technology, see [Responsible AI][RAI].

<!--links-->

[CSP-1]: /windows/client-management/mdm/policy-csp-windowsai
[M365-1]: /microsoft-365/admin/misc/organizational-messages-microsoft-365?view=o365-worldwide
[INT-1]: /mem/intune/configuration/settings-catalog
[KB-1]: https://support.microsoft.com/topic/9c5bc200-52b6-4c1a-be70-80df6bbfe9c3
[RAI]: https://www.microsoft.com/ai/responsible-ai
