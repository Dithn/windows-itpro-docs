---
title: Deploy Microsoft Connected Cache software to a Windows host machine
description: Details on how to deploy Microsoft Connected Cache for Enterprise and Education cache software to a Windows host machine.
author: chrisjlin
ms.author: lichris
manager: naengler
ms.service: windows-client
ms.subservice: itpro-updates
ms.topic: how-to
ms.date: 08/06/2025
appliesto: 
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 11</a>
- ✅ <a href=https://learn.microsoft.com/windows/deployment/do/waas-microsoft-connected-cache target=_blank>Microsoft Connected Cache for Enterprise and Education</a>	
---

# Deploy Microsoft Connected Cache caching software to a Windows host machine

This article describes how to deploy Microsoft Connected Cache for Enterprise and Education caching software to a Windows host machine.

Deploying Connected Cache to a Windows host machine requires designating a [Group Managed Service Account (gMSA)](/windows-server/security/group-managed-service-accounts/getting-started-with-group-managed-service-accounts), a [local user account](https://support.microsoft.com/topic/20de74e0-ac7f-3502-a866-32915af2a34d), a domain user account, or a service account as the Connected Cache runtime account. This prevents tampering with the Connected Cache container and the cached content on the host machine.

> [!NOTE]
> If you plan to designate a Group Managed Service Account (gMSA) as the Connected Cache runtime account, ensure that you're logged on to the host machine as a **domain-joined** account when following the deployment steps below.

Before deploying Connected Cache to a Windows host machine, ensure that the host machine meets all [requirements](mcc-ent-prerequisites.md), and that you have [created and configured your Connected Cache Azure resource](mcc-ent-create-resource-and-cache.md).

For Connected Cache deployment to succeed, you must allow direct calls to the Delivery Optimization service from your Connected Cache host machines. When using a TLS-inspecting proxy, you must configure your proxy/host machine to allow calls to and from the Delivery Optimization service (*.prod.do.dsp.mp.microsoft.com) to bypass the proxy's interception, otherwise the certificate chain will be broken and cache node deployment and operation will fail.

## Steps to deploy Connected Cache node to Windows

# [Azure portal](#tab/portal)

1. Within the Azure portal, navigate to the **Deployment** tab of your cache node and copy the deployment command.
1. Download and install the Connected Cache Windows application to your host machine by running the following command in an elevated PowerShell window:

   ```powershell-interactive
   Add-AppxPackage "https://aka.ms/do-mcc-ent-windows-x64"
   ```

1. You can verify that the Connected Cache app has been installed by running the following command:

   ```powershell-interactive
   Get-AppxPackage Microsoft.DeliveryOptimization
   ```

1. Confirm that the Connected Cache app has placed the Connected Cache installation scripts by running the following command:

   ```powershell-interactive
   deliveryoptimization-cli mcc-get-scripts-path
   ```

   This command should return a path to the Connected Cache **scripts directory**, such as `C:\Program Files\...\deliveryoptimization-cli`. **Do not** move the Connected Cache scripts directory to a different location, as the deployment scripts won't be updateable if they're moved to a different path.

1. Open a PowerShell window *as administrator* on the host machine and set the Execution Policy to *Unrestricted* to allow the deployment scripts to run. The administrator account used to proceed through this cache node deployment process **cannot be the same as the Connected Cache runtime account**.

1. Create a `$User` PowerShell variable containing the username of the account you intend to designate as the Connected Cache runtime account.

   * For gMSAs, the `$User` PowerShell variable should be formatted as `"Domain\Username$"`. You'll also need to be logged in as a domain-joined account when you run the deployment command.
   * For local user accounts, `$User` PowerShell variable should be formatted as `"LocalMachineName\Username"`. For domain user and service accounts, `$User` should be formatted as `"Domain\Username"`. For local user, domain user, and service accounts you'll also need to create a [PSCredential Object](/dotnet/api/system.management.automation.pscredential) named `$myLocalAccountCredential`.

   >[!Note]
   > You'll need to apply a local security policy to permit the Connected Cache runtime account to `Log on as a batch job`. Make sure to save your runtime account information, as you'll need it for troubleshooting and uninstallation.

1. In the same PowerShell window, run the deployment command that you copied from the Azure portal.

   >[!Note]
   > If you are deploying your cache node to a Windows host machine that uses a TLS-inspecting proxy (e.g. ZScaler), ensure that you've [configured the proxy settings](mcc-ent-create-resource-and-cache.md#proxy-settings) for your cache node, then place the proxy certificate file (.pem) in your desired **installationFolder** path and add `-proxyTlsCertificatePemFileName "mycert.pem"` to the deployment command.
   > For example, place the .pem file in `C:\mccwsl01\mycert.pem` and add `-proxyTlsCertificatePemFileName "mycert.pem"` to the deployment command.

# [Azure CLI](#tab/cli)

To deploy a cache node programmatically, you need to use Azure CLI to get the cache node's deployment details before running the deployment command on the host machine.

1. To get the cache node's deployment details, use `az mcc ent node get-deployment-details`.

   ```azurecli-interactive
   az mcc ent node get-deployment-details --cache-node-name mycachenode --mcc-resource-name mymccresource --resource-group myrg
   ```

1. Save the resulting output. These values must be passed as parameters within the deployment command.
1. Download and install the Connected Cache Windows application to your host machine by running the following command in an elevated PowerShell window:

   ```powershell-interactive
   Add-AppxPackage "https://aka.ms/do-mcc-ent-windows-x64"
   ```

1. You can verify that the Connected Cache app has been installed by running the following command:

   ```powershell-interactive
   Get-AppxPackage Microsoft.DeliveryOptimization
   ```

1. Open a PowerShell window *as administrator* on the host machine and set the Execution Policy to *Unrestricted* to allow the deployment scripts to run.
1. Create a `$User` PowerShell variable containing the username of the account you intend to designate as the Connected Cache runtime account.

   * For gMSAs, the `$User` PowerShell variable should be formatted as `"Domain\Username$"`. You'll also need to be logged in as a domain-joined account when you run the deployment command.
   * For local user accounts, `$User` PowerShell variable should be formatted as `"LocalMachineName\Username"`. For domain user and service accounts, `$User` should be formatted as `"Domain\Username"`. For local user, domain user, and service accounts you'll also need to create a [PSCredential Object](/dotnet/api/system.management.automation.pscredential) named `$myLocalAccountCredential`.

   >[!Note]
   > You'll need to apply a local security policy to permit the Connected Cache runtime account to `Log on as a batch job`. Make sure to save your runtime account information, as you'll need it for troubleshooting and uninstallation.

1. Replace the values in the following deployment command before running it on the host machine. Parameters in square brackets are optional depending on your cache node configuration.

   ```powershell-interactive
   Push-Location (deliveryoptimization-cli mcc-get-scripts-path); ./deploymcconwsl.ps1 -installationFolder c:\mccwsl01 -customerid <GUID> -cachenodeid <GUID> -customerkey <GUID> -registrationkey <GUID> -cacheDrives "/var/mcc,<SIZE>" -mccRunTimeAccount $User [-mccLocalAccountCredential $myLocalAccountCredential] [-rebootBypass $true] [-proxyTlsCertificatePemFileName "mycert.pem"] [-shouldUseProxy $true -proxyurl "http://proxy.example.com:8080"]
   ```

   >[!Note]
   > If you are deploying your cache node to a Windows host machine that uses a TLS-inspecting proxy (e.g. ZScaler), ensure that you've [configured the proxy settings](mcc-ent-create-resource-and-cache.md#proxy-settings) for your cache node, then place the proxy certificate file (.pem) in your desired **installationFolder** path and add `-proxyTlsCertificatePemFileName "mycert.pem"` to the deployment command.
   > For example, place the .pem file in `C:\mccwsl01\mycert.pem` and add `-proxyTlsCertificatePemFileName "mycert.pem"` to the deployment command.

---

## Windows deployment command parameters

| Parameter | Description |
|-----------|-------------|
| `-installationFolder` | The folder where the Connected Cache is installed. This can be changed to any desired path on the host machine.|
| `-customerid` | The unique ID for your Connected Cache Azure resource. This is available in the Azure portal on the **Overview** page. |
| `-cachenodeid` | The unique ID for your Connected Cache node. This is available in the Azure portal on the **Cache Node Management** page. |
| `-customerkey` | The unique customer key for your Connected Cache Azure resource. This is available in the Azure portal on the **Cache Node Configuration** page. |
| `-registrationkey` | The unique registration key for your Connected Cache node. This is available in the Azure portal on the **Cache Node Configuration** page. This registration key will be refreshed after each successful deployment attempt of this cache node. |
| `-cacheDrives` | The amount of storage that the cache node uses. This should be formatted as `"/var/mcc,<SIZE>"`, where `<SIZE>` is the desired size of the cache node in GB. |
| `-mccRunTimeAccount` | The account that runs the Connected Cache software. This should be a PowerShell variable containing the username of the account you intend to designate as the Connected Cache runtime account. For example, `$User = "LocalMachineName\Username"` for a local user account. If you're using a Group Managed Service Account (gMSA), it should be formatted as `"Domain\Username$"`. |
| `-mccLocalAccountCredential` | A PowerShell credential object for the Connected Cache runtime account. This is only needed if you're using a local user account, domain user account, or service account. For example, `$myLocalAccountCredential = Get-Credential`. |
| `-rebootBypass` | If set to `$true`, the Connected Cache installation process won't check for pending reboot on the host machine. This is optional and defaults to `$false`. |
| `-shouldUseProxy` | If set to `$true`, the deployed cache node communicates through your proxy server. This is optional and defaults to `$false`. |
| `-proxyurl` | The URL of the proxy server for the cache node use. This is optional and only needed if you're using a proxy server. For example, `-proxyurl "http://proxy.example.com:8080"`. |
| `-proxyTlsCertificatePemFileName` | The name of the proxy certificate file in PEM format. This is optional and only needed if you're using a TLS-inspecting proxy. For example, `-proxyTlsCertificatePemFileName "mycert.pem"`. The .pem file must be placed in the **installationFolder** path. |

## Steps to point Windows client devices at Connected Cache node

Once you have successfully deployed Connected Cache to your Windows host machine, you need to configure your Windows client devices to request Microsoft content from the Connected Cache node.

You can do this by setting the [DOCacheHost or DOCacheHostSource policies via Intune](./waas-delivery-optimization-reference.md#cache-server-hostname).

## Next step

> [!div class="nextstepaction"]
> [Verify cache node functionality](mcc-ent-verify-cache-node.md)

## Related content

* [Deploy to a Linux host machine](mcc-ent-deploy-to-linux.md)
* [Uninstall Connected Cache node](mcc-ent-uninstall-cache-node.md)
