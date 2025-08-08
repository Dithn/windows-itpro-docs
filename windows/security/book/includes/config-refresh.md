---
author: paolomatarazzo
ms.author: paoloma
ms.date: 12/11/2024
ms.topic: include
---

## :::image type="icon" source="../images/new-button-title.svg" border="false"::: Config Refresh

With traditional group policy, policy settings are refreshed on a PC when a user signs in and every 90 minutes by default. Administrators can adjust that timing to be shorter to ensure that the policy settings are compliant with the management settings set by IT.

By contrast, with a device management solution like Microsoft Intune<sup>[\[4\]](../conclusion.md#footnote4)</sup>, policies are refreshed when a user signs in and then at eight-hours interval by default. But policy settings are migrated from GPO to a device management solution, one remaining gap is the longer period between the reapplication of a changed policy.

Config Refresh allows settings in the Policy configuration service provider (CSP) that drift due to misconfiguration, registry edits, or malicious software on a PC to be reset to the value the administrator intended every 90 minutes by default. It's configurable to refresh every 30 minutes if desired. The Policy CSP covers hundreds of settings that were traditionally set with group policy and are now set through Mobile Device Management (MDM) protocols.

Config Refresh can also be paused for a configurable period of time, after which it will be reenabled. This is to support scenarios where a helpdesk technician might need to reconfigure a device for troubleshooting purposes. It can also be resumed at any time by an administrator.

[!INCLUDE [learn-more](learn-more.md)]

- [Config Refresh](https://techcommunity.microsoft.com/blog/windows-itpro-blog/intro-to-config-refresh-%e2%80%93-a-refreshingly-new-mdm-feature/4176921)
