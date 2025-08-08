---
title: Firewall and network protection in Windows Security
description: Use the Firewall & network protection section to see the status of and make changes to firewalls and network connections for the machine.
ms.date: 04/15/2025
ms.topic: how-to
---

# Firewall and network protection

The **Firewall & network protection** section contains information about the firewalls and network connections used by the machine, including the status of Windows Firewall and any other non-Microsoft firewalls. IT administrators and IT pros can get configuration guidance from the [Windows Firewall with Advanced Security documentation library](../../network-security/windows-firewall/index.md).

This section can be hidden from users of the machine. This information is useful if you don't want users in your organization to have access to user-configured options for the features shown in the section.

## Hide the Firewall & network protection section

You can choose to hide the entire section by using Group Policy. When hidden, this section doesn't appear on the home page of **Windows Security**, and its icon isn't shown on the navigation bar on the side.

> [!IMPORTANT]
> You must have Windows 10, version 1709 or later. The ADMX/ADML template files for earlier versions of Windows don't include these Group Policy settings.

1. On your Group Policy management machine, open the Group Policy Management Console. Right-click the Group Policy Object (GPO) you want to configure and select **Edit**.
1. In **Group Policy Management Editor**, go to **Computer configuration** and select **Administrative templates**.
1. Expand the tree to **Windows components > Windows Security > Firewall and network protection**.
1. Open the **Hide the Firewall and network protection area** setting and set it to **Enabled**. Select **OK**.
1. [Deploy](/windows/win32/srvnodes/group-policy) the updated GPO as you normally do.

> [!NOTE]
> If you hide all sections, then **Windows Security** shows a restricted interface, as in the following screenshot:
>
> ![Screenshot of the Windows Security with all sections hidden by Group Policy.](images/wdsc-all-hide.png)
