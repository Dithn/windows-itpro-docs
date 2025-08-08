---
title: Deploy Microsoft Connected Cache software to a Linux host machine
description: Details on how to deploy Microsoft Connected Cache for Enterprise and Education cache software to a Linux host machine.
author: chrisjlin
ms.author: lichris
manager: naengler
ms.service: windows-client
ms.subservice: itpro-updates
ms.topic: how-to
ms.date: 07/23/2025
appliesto: 
- ✅ Supported Linux distributions
- ✅ <a href=https://learn.microsoft.com/windows/deployment/do/waas-microsoft-connected-cache target=_blank>Microsoft Connected Cache for Enterprise and Education</a>	
---

# Deploy Microsoft Connected Cache caching software to a Linux host machine

This article describes how to deploy Microsoft Connected Cache for Enterprise and Education caching software to a Linux host machine.

Before deploying Connected Cache to a Linux host machine, ensure that the host machine meets all [requirements](mcc-ent-prerequisites.md), and that you have [created and configured your Connected Cache Azure resource and cache node](mcc-ent-create-resource-and-cache.md).

For Connected Cache deployment to succeed, you must allow direct calls to the Delivery Optimization service from your Connected Cache host machines. When using a TLS-inspecting proxy, you must configure your proxy/host machine to allow calls to and from the Delivery Optimization service (*.prod.do.dsp.mp.microsoft.com) to bypass the proxy's interception, otherwise the certificate chain will be broken and cache node deployment and operation will fail.

## Steps to deploy Connected Cache cache node to Linux

# [Azure portal](#tab/portal)

1. Within the Azure portal, navigate to the **Deployment** tab of your cache node and copy the deployment command.
1. Download the Linux deployment package using the option at the top of the Cache Node Configuration page and extract the package onto the host machine.
1. Open a command line window *as administrator* on the host machine, then change directory to the extracted deployment package.

    >[!Note]
    >* If you're deploying your cache node to a host machine that uses a TLS-inspecting proxy (e.g. ZScaler), ensure that you've [configured the proxy settings](mcc-ent-create-resource-and-cache.md#proxy-settings) for your cache node, then place the proxy certificate file (.pem) in the extracted deployment package directory and add `proxytlscertificatepath="/path/to/pem/file"` to the deployment command.

1. Set access permissions to allow the `deploymcc.sh` script within the deployment package directory to execute.
1. Run the deployment command on the host machine.

>[!NOTE]
> After redeploying a Linux cache node so that it's migrated to the GA release container, the user must run `chmod 777 -R /cachedrivepath` and then restart the Connected Cache container `sudo iotedge restart MCC`.
> Otherwise the redeployed node will be up and running, but requests for content will fail.

# [Azure CLI](#tab/cli)

To deploy a cache node programmatically, you need to use Azure CLI to get the cache node's deployment details and then run the deployment command on the host machine.

1. To get the cache node's deployment details, use `az mcc ent node get-deployment-details`

   ```azurecli-interactive
   az mcc ent node get-provisioning-details --cache-node-name mycachenode --mcc-resource-name mymccresource --resource-group myrg
   ```

1. Save the resulting output. These values are passed as parameters within the deployment command.
1. Download and extract the [Connected Cache deployment package for Linux](https://aka.ms/MCC-Ent-InstallScript-Linux) to your host machine.
1. Open a command line window *as administrator* on the host machine, then change directory to the extracted deployment package.

    > [!Note]
    >* If you're deploying your cache node to a host machine that uses a TLS-inspecting proxy (e.g. ZScaler), ensure that you've [configured the proxy settings](mcc-ent-create-resource-and-cache.md#proxy-settings) for your cache node, then place the proxy certificate file (.pem) in the extracted deployment package directory and then add `proxytlscertificatepath="/path/to/pem/file"` to the deployment command.

1. Set access permissions to allow the `deploymcc.sh` script within the deployment package directory to execute.
1. Replace the values in the following deployment command before running it on the host machine.

   ```azurepowershell-interactive
   sudo ./deploymcc.sh customerid="enter mccResourceId here" cachenodeid="enter cacheNodeId here" customerkey=" enter customerKey here " registrationkey="enter registrationKey here" drivepathandsizeingb="enter physicalPath value,enter sizeInGb value here" shoulduseproxy="enter true if present, enter false if not" proxyurl=http://enter proxy hostname:enter port
   ```

---

## Linux deployment command parameters

| Parameter | Description |
|-----------|-------------|
| `-customerid` | The unique ID for your Connected Cache Azure resource. This is available in the Azure portal on the **Overview** page. |
| `-cachenodeid` | The unique ID for your Connected Cache node. This is available in the Azure portal on the **Cache Node Management** page. |
| `-customerkey` | The unique customer key for your Connected Cache Azure resource. This is available in the Azure portal on the **Cache Node Configuration** page. |
| `-registrationkey` | The unique registration key for your Connected Cache node. This is available in the Azure portal on the **Cache Node Configuration** page. This registration key will be refreshed after each successful deployment attempt of this cache node. |
| `-drivepathandsizeingb` | The drive path and amount of storage that the cache node will use. This should be formatted as `"<PATH>,<SIZE>"`, where `<PATH>` is the desired drive path and `<SIZE>` is the desired size of the cache node in GB. You can specify multiple drives using `"<PATH1>,<SIZE1>,<PATH2><SIZE2>..."`|
| `-rebootBypass` | If set to `$true`, the Connected Cache installation process won't check for pending reboot on the host machine. This is optional and defaults to `$false`. |
| `-shouldUseProxy` | If set to `$true`, the deployed cache node communicates through your proxy server. This is optional and defaults to `$false`. |
| `-proxyurl` | The URL of the proxy server for the cache node use. This is optional and only needed if you're using a proxy server. For example, `-proxyurl "http://proxy.example.com:8080"`. |
| `-proxytlscertificatepath` | The path of the proxy certificate file in PEM format. This is optional and only needed if you're using a TLS-inspecting proxy. For example, `-proxytlscertificatepath="/path/to/pem/file"`. |

## Steps to point Windows client devices at Connected Cache node

Once you have successfully deployed Connected Cache to your Linux host machine, you need to configure your Windows client devices to request Microsoft content from the Connected Cache node.

You can do this by setting the [DOCacheHost or DOCacheHostSource policies via Intune](./waas-delivery-optimization-reference.md#cache-server-hostname).

## Next step

> [!div class="nextstepaction"]
> [Verify cache node functionality](mcc-ent-verify-cache-node.md)

## Related content

- [Deploy to a Windows host machine](mcc-ent-deploy-to-windows.md)
- [Uninstall Connected Cache node](mcc-ent-uninstall-cache-node.md)
