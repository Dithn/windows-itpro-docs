---
title: Quick Machine Recovery
description: Learn about quick machine recovery and how to configure it with the RemoteRemediation configuration service provider (CSP).
ms.topic: how-to
ms.date: 06/02/2025
ms.author: paoloma
author: paolomatarazzo
appliesto:
  - "✅ <a href=\"https://learn.microsoft.com/windows/release-health/supported-versions-windows-client\" target=\"_blank\">Windows 11</a>"
---

# Quick machine recovery

Starting with Windows 11, version 24H2 with [KB5062660][KB-1], quick machine recovery is a feature that enables the recovery of Windows devices when they encounter critical errors that prevent them from booting. This feature can automatically search for remediations in the cloud and recover from widespread boot failures, significantly reducing the burden on IT administrators when multiple devices are affected.

Building on the foundation of [Startup Repair][SMC-1], quick machine recovery uses a secure and connected [Windows Recovery Environment][SMC-2] to scan Windows Update for remediation options. This allows devices to be recovered without requiring manual intervention.

## How it works

There are two main settings of quick machine recovery: cloud remediation and auto remediation.

### Cloud remediation

:::row:::
    :::column span="3":::
Cloud remediation is the process of using Windows Update to find remediations and fix issues on devices:

- When enabled, devices connect to the network and utilize Windows Update during recovery scenarios
- When disabled, Windows uses Startup Repair as a local recovery option
    :::column-end:::
    :::column span="1":::
:::image type="content" source="images/quick-machine-recovery-network.png" alt-text="Screenshot of quick machine recovery boot while attempting to connect to the network." border="false" lightbox="images/quick-machine-recovery-network.png":::
    :::column-end:::
:::row-end:::

> [!NOTE]
> Quick machine recovery is a best-effort feature. It might not always be able to find a solution for every issue.

### Auto remediation

:::row:::
    :::column span="3":::

Auto remediation allows you to automate the recovery process:

  - When enabled, the device connects automatically to Windows Update and tries to find a remediation. If a solution isn't found on the first attempt, the device retries without requiring manual intervention
    :::column-end:::
    :::column span="1":::
:::image type="content" source="images/auto-remediation.png" alt-text="Screnshot of the Windows Recovery Environment in the auto remediation screen, showing that the device retries to find a solution." border="false" lightbox="images/auto-remediation.png":::
:::row-end:::
:::row:::
    :::column span="3":::
  - When disabled or not configured, the device requires manual intervention to continue the recovery process

    :::column-end:::
    :::column span="1":::
:::image type="content" source="images/quick-machine-recovery-winre.png" alt-text="Screnshot of Windows Recovery Environment showing the quick machine recovery option." border="false" lightbox="images/quick-machine-recovery-winre.png":::

:::row-end:::

### Quick machine recovery process

Here are the phases of the quick machine recovery process:

1. **Device crash**: When the device fails to boot repeatedly, the system automatically detects the issue and initiates the recovery process
1. **Boot to recovery**: The device boots into the recovery environment to initiate the quick machine recovery process
1. **Network connection**: After a network connection is established, the device scans Windows Update for remediations
1. **Remediation**
    - If no solution is found, the system retries the process based on the configured retry scanning intervals and time-outs
    - If a solution is found, the system downloads and applies it
1. **Reboot**: After a remediation is applied, the device reboots:
    - If the solution is successful, the device boots into Windows
    - If the solution fails, the device reboots into the recovery environment again and the process repeats from step 2

:::image type="content" source="images/diagram.png" alt-text="Diagram of quick machine recovery showing the five phases of recovery." border="false" lightbox="images/diagram.png":::

## Configuration

Cloud remediation is enabled by default on Windows Home edition devices, while auto remediation is turned off by default. For Windows Pro and Enterprise editions, both cloud remediation and auto remediation are disabled by default. Organizations can decide the best configuration for their devices based on their specific needs.

The configuration options consist of:

- Enable or disable cloud remediation
- Enable or disable auto remediation
- Configure auto remediation scanning intervals and time-outs to optimize remediation triggers
- Configure network connections to ensure smooth recovery workflows
    > [!IMPORTANT]
    > Currently, only wired and WPA/WPA2 password-based Wi-Fi networks are supported. Ensure your network uses this configuration for compatibility.

[!INCLUDE [tab-intro](../../../includes/configure/tab-intro.md)]

# [:::image type="icon" source="../images/icons/intune.svg" border="false"::: **Intune**](#tab/intune)

[!INCLUDE [intune-settings-catalog-1](../../../includes/configure/intune-settings-catalog-1.md)]

| Category | Setting name |
|--|--|
| **Remote Remediation** | Enable Cloud Remediation |
| **Remote Remediation** | Enable Cloud Remediation > Enable Auto Remediation |
| **Remote Remediation** | Enable Cloud Remediation > Enable Auto Remediation > Set Time To Reboot |
| **Remote Remediation** | Enable Cloud Remediation > Enable Auto Remediation > Set Retry Interval |
| **Remote Remediation** | Enable Cloud Remediation > Enable Auto Remediation > Network SSID |
| **Remote Remediation** | Enable Cloud Remediation > Enable Auto Remediation > Network Password |
| **Remote Remediation** | Enable Cloud Remediation > Enable Auto Remediation > Network Password Encryption Type |
| **Remote Remediation** | Enable Cloud Remediation > Enable Auto Remediation > Network Password Encryption Store |

[!INCLUDE [intune-settings-catalog-2](../../../includes/configure/intune-settings-catalog-2.md)]

# [:::image type="icon" source="../images/icons/csp.svg" border="false"::: **CSP**](#tab/csp)

You can configure devices with the [RemoteRemediation CSP][CSP-1].

### Cloud remediation configuration

Enable or disable cloud remediation using the following settings:

| Setting |
|--|
|- **OMA-URI:** `./Device/Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/EnableCloudRemediation`<br>- **Data type:** Boolean<br>- **Value:** `True`<br>- **Description**: When set to `True`, cloud remediation is enabled. |

### Auto remediation configuration

Configure the following settings to customize the auto remediation experience:

| Setting |
|--|
|- **OMA-URI:** `./Device/Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/AutoRemediationSettings/EnableAutoRemediation`<br>- **Data type:** Boolean<br>- **Value:** `True`<br>- **Description**: When set to `True`, auto remediation is enabled. |
|- **OMA-URI:** `./Device/Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/AutoRemediationSettings/SetTimeToReboot`<br>- **Data type:** Integer<br>- **Value:** 1-4320 (default = 180)<br>- **Description**: Configure the time to reboot (in minutes) during auto remediation. The maximum time to reboot possible is 72 hours.|
|- **OMA-URI:** `./Device/Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/AutoRemediationSettings/SetRetryInterval`<br>- **Data type:** Integer<br>- **Value:** 1-4320 (default = 30)<br>- **Description**: Configure the retry interval (in minutes) during auto remediation. The retry interval shouldn't be higher than the time to reboot.|

### Wi-Fi network connection configuration

To configure the Wi-Fi network connection used during recovery, use the following settings:

|Setting|
|--|
|- **OMA-URI:** `./Device/Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/NetworkSettings/NetworkCredentials/NetworkSSID`<br>- **Data type:** string<br>- **Value:** Wi-Fi network Service Set Identifier (SSID)|
|- **OMA-URI:** `./Device/Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/NetworkSettings/NetworkCredentials/NetworkPassword`<br>- **Data type:** string<br>- **Value:** Wi-Fi network password|
|- **OMA-URI:** `./Device/Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/NetworkSettings/NetworkCredentials/NetworkPasswordEncryptionType`<br>- **Data type:** Integer<br>- **Value:** `0` = The password isn't encrypted; `1` = The password is encrypted with the MDM certificate, `2` = The password is encrypted with custom certificate. When this value is used, you must also specify the custom store name in the `NetworkPasswordEncryptionStore` node.|
|- **OMA-URI:** `./Device/Vendor/MSFT/RemoteRemediation/CloudRemediationSettings/NetworkSettings/NetworkCredentials/NetworkPasswordEncryptionStore`<br>- **Data type:** string<br>- **Value:** When a value of `2` is contained in `NetworkPasswordEncryptionType`, specify the store name where the certificate for decrypting the Network Password is stored.|

# [:::image type="icon" source="../images/icons/cmd.svg"::: **Command prompt**](#tab/cmd)

To configure quick machine recovery using the command line, you must create an XML file with the desired settings and then use the `reagentc.exe` command to apply those settings.

Use the following command to apply the settings:

```cmd
reagentc.exe /setrecoverysettings /path settings.xml
```

Where `settings.xml` is the path to the XML file containing the quick machine recovery configuration.

### XML file example

The following XML file example configures quick machine recovery with the following settings:

- The Wi-Fi network has an SSID `ContosoWiFi` and a password `ContosoWiFiPassword`
- Cloud remediation is enabled (`state="1"`)
- Auto remediation is enabled (`state="1"`)
  - The `totalwaittime` is set to 2,400 minutes (40 hours) and the `waitinterval` is set to 120 minutes (2 hours). Once configured, the system waits for 40 hours before rebooting, and it checks for remediation every 2 hours

```xml
<?xml version='1.0' encoding='utf-8'?>

<WindowsRE>
    <WifiCredential>
        <Wifi ssid="ContosoWiFi" password="ContosoWiFiPassword" />
    </WifiCredential>
    <CloudRemediation state="1" />
    <AutoRemediation state="1" totalwaittime="2400" waitinterval="120"/>
</WindowsRE>
```

### Remove recovery settings

To remove the configured recovery settings, run the following command from an elevated command prompt:

```cmd
reagentc.exe /clearrecoverysettings
```

# [:::image type="icon" source="../images/icons/settings-app.svg"::: **Settings**](#tab/settings)

Here are the steps to configure quick machine recovery from Settings:

1. Open Settings and go to **System** > **Recovery**, or use the following shortcut:

    > [!div class="nextstepaction"]
    >
    > [Recovery](ms-settings:recovery)

1. Select **Quick machine recovery**
1. To enable quick machine recovery, turn the **Quick machine recovery** toggle to **On**
1. Configure the retry and restart intervals as needed

 :::image type="content" source="images/quick-machine-recovery-settings.png" border="false" lightbox="images/quick-machine-recovery-settings.png" alt-text="Screenshot of the Setting app - Recovery - Quick machine recovery - showing the quick machine recovery options.":::

---

### Verify Recovery Settings

To check the configured recovery settings, run the following command from an elevated command prompt:

```cmd
reagentc.exe /getrecoverysettings
```

Output example:

```console
C:\>reagentc.exe /getrecoverysettings
<?xml version='1.0' encoding='utf-8'?>

<WindowsRE>
    <WifiCredential>
        <Wifi ssid="ContosoWiFi" password="ContosoWiFiPassword" />
    </WifiCredential>
    <CloudRemediation state="1" />
    <AutoRemediation state="1" totalwaittime="2400" waitinterval="120"/>
</WindowsRE>

REAGENTC.EXE: Operation Successful.
```

## Test mode

:::row:::
    :::column span="3":::
Quick machine recovery offers a *test mode*, providing a controlled, simulated environment to experience the auto remediation process without triggering an actual system failure. Test mode allows you to verify that the recovery experience functions as expected before deployment to production systems.
    :::column-end:::
    :::column span="1":::
:::image type="content" source="images/quick-machine-recovery-test-mode.png" alt-text="Screenshot of the Windows boot screen where quick machine recovery is attempting to connect to the network." border="false" lightbox="images/quick-machine-recovery-test-mode.png":::
    :::column-end:::
:::row-end:::

To simulate the quick machine recovery experience, use the following commands from an elevated command prompt:

1. Enable test mode:
    ```cmd
    reagentc.exe /SetRecoveryTestmode
    ```
1. Configure Windows to boot to Windows Recovery Environment on the next boot:
    ```cmd
    reagentc.exe /BootToRe
    ```
1. Reboot your device. The system goes through autoremediation of a simulated crash and reboots back to Windows

    > [!NOTE]
    > If after reboot the device goes into Windows RE instead of starting test mode, follow these steps:
    >
    >   1. In Windows RE, select **Continue** to boot Windows normally
    >   1. In Windows, execute the two commands:
    >
    >       - `reagentc.exe /Disable`
    >       -  `reagentc.exe /Enable`
    >
    >   1. Retry the quick machine recovery simulation starting from step 1

## Verify remediation

If a relevant remediation is applied to the device, it appears under **Settings** > **Windows Update** > **[Update history](ms-settings:windowsupdate-history)**, listed within the **Quality updates** section.

:::image type="content" source="images/update-history.png" border="false" lightbox="images/update-history.png" alt-text="Screenshot of the Setting app - Windows Update - showing the installation of a quick machine recovery update.":::

### :::image type="icon" source="../images/icons/feedback.svg" border="false"::: Provide feedback

To provide feedback for quick machine recovery, open [**Feedback Hub**][FHUB] and use the category **Recovery and Uninstall** > **Quick Machine Recovery**.

<!--links-->

[SMC-1]: https://support.microsoft.com/topic/85deb0b9-fa3d-44a3-a3d0-d0f1515c2c9b
[SMC-2]: https://support.microsoft.com/topic/0eb14733-6301-41cb-8d26-06a12b42770b
[FHUB]: feedback-hub://?tabid=2&newFeedback=true&feedbackType=1
[CSP-1]: /windows/client-management/mdm/remoteremediation-csp
[INT-1]: /mem/intune/configuration/settings-catalog
[KB-1]: https://support.microsoft.com/help/5062660
