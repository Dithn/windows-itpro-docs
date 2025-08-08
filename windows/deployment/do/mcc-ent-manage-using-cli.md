---
title: Manage Microsoft Connected Cache nodes using CLI
description: Details on how to manage Microsoft Connected Cache for Enterprise cache nodes via Azure CLI commands.
ms.service: windows-client
ms.subservice: itpro-updates
ms.topic: how-to
manager: bpardi
ms.author: nidos
author: doshnid
ms.reviewer: mstewart
ms.collection: tier3
appliesto:
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 11</a>
- ✅ <a href=https://learn.microsoft.com/windows/release-health/supported-versions-windows-client target=_blank>Windows 10</a>
- ✅ <a href=https://learn.microsoft.com/windows/deployment/do/waas-microsoft-connected-cache target=_blank>Microsoft Connected Cache for Enterprise</a>
ms.date: 07/23/2025
---

# Manage cache nodes using CLI

This article outlines how to create, configure, and deploy Microsoft Connected Cache for Enterprise cache nodes using Azure CLI.

## Prerequisites

1. **Install Azure CLI**: [How to install the Azure CLI](/cli/azure/install-azure-cli)
1. **Install Connected Cache extension**: Install Connected Cache extension via the command below

```azurecli-interactive
az extension add --name mcc
```

To learn more about installing extensions, see [Install the Connected Cache extension.](/cli/azure/azure-cli-extensions-overview#how-to-install-extensions)

### 1. Create a Resource group

The first step is to create a resource group if you don't already have one.
An Azure resource group is a logical container into which Azure resources are deployed and managed.

To create a resource group, use `az group create`. You can find more details on this CLI command [here](/cli/azure/group#az-group-create).

```azurecli-interactive
az group create --name myrg --location westus
```

Once the resource group is created, you need to create a Microsoft Connected Cache for Enterprise Azure resource.

### 2. Create a Connected Cache Azure resource

A Connected Cache Azure resource is a top-level Azure resource under which cache nodes can be created.

To create a Connected Cache Azure resource, use `az mcc ent resource create`

```azurecli-interactive
az mcc ent resource create --mcc-resource-name mymccresource --resource-group myrg
```

>[!IMPORTANT]
>In the output, look for operationStatus. **operationStatus = Succeeded** indicates that our services have successfully started creating your Connected Cache resource.

The next step is to create a cache node under this resource.

### 3. Create a cache node

To create a cache node, use `az mcc ent node create`

```azurecli-interactive
az mcc ent node create --cache-node-name mycachenode --mcc-resource-name mymccresource --resource-group myrg --host-os <linux or windows>
```

>[!IMPORTANT]
>In the output, look for operationStatus. **operationStatus = Succeeded** indicates that our services have successfully started creating cache node.

### 4. Confirm cache node creation

Before you can start configuring your cache node, you need to confirm that the cache node was successfully created.

To confirm cache node creation, use `az mcc ent node show`

```azurecli-interactive
az mcc ent node show --cache-node-name mycachenode --mcc-resource-name mymccresource --resource-group myrg
```

>[!IMPORTANT]
>In the output look for cacheNodeState. If **cacheNodeState = Not Configured**, you can continue with cache node configuration.
>If **cacheNodeState = Registration in Progress**, then the cache node is still in process of being created. Wait for a minute or two more and run the command again.

Once successful cache node creation is confirmed, you can proceed to configure the cache node.

### 5. Configure cache node

To configure your cache node, use `az mcc ent node update`

The below example configures a Linux cache node with proxy enabled:

```azurecli-interactive
az mcc ent node update --cache-node-name <mycachenode> --mcc-resource-name <mymccresource> --resource-group <myrg>
--cache-drive "[{physical-path:</physical/path>,size-in-gb:<size of cache drive>},{</physical/path>,size-in-gb:<size of cache drive>}...]"> --proxy <enabled> --proxy-host <"proxy host name"> --proxy-port <proxy port>  --auto-update-day <day of week> --auto-update-time <time of day> --auto-update-week <week of month> --auto-update-ring <update ring>
```

Remember that the minimum size of a cache drive is 50 GB. You can specify multiple cache drives for Linux-hosted cache nodes by adding additional entries to the `--cache-drive` parameter.

>[!Note]
>* For Windows-hosted cache nodes, the physical path of the cache drive must be **/var/mcc**.
>* In the output, look for operationStatus. **operationStatus = Succeeded** indicates that our services have successfully updated the cache node. You will also see that cacheNodeState will show *Not Provisioned*.
>* Save values for physicalPath, sizeInGb, proxyPort, and proxyHostName as these values will be needed to construct the deployment command.

### 6. Get deployment details for the cache node

After successfully configuring the cache node, the next step is to deploy the cache node to a host machine. To deploy the cache node, you need to create a deployment command using the cache nodes unique identifiers.

To get the relevant information for the deployment command, use `az mcc ent node get-deployment-details`.

```azurecli-interactive
az mcc ent node get-deployment-details --cache-node-name mycachenode --mcc-resource-name mymccresource --resource-group myrg
```

>[!IMPORTANT]
>* Save the resulting values for cacheNodeId, customerKey, mccResourceId, registrationKey. These GUIDs are needed for the deployment command.
>* In the output look for cacheNodeState. If **cacheNodeState = Not Provisioned**, you can continue with cache node deployment.
>* If **cacheNodeState = Not Configured**, then the cache node hasn't been configured. Configure the cache node before deployment.

## Next step

To deploy the cache node to a **Windows** host machine, see
>[!div class="nextstepaction"]
>[Deploy cache node to Windows](mcc-ent-deploy-to-windows.md)

To deploy the cache node to a **Linux** host machine, see
>[!div class="nextstepaction"]
>[Deploy cache node to Linux](mcc-ent-deploy-to-linux.md)

### Example script to bulk create and configure multiple cache nodes

Below is a pseudocode example of how to script bulk creation and configuration of a Connected Cache Azure resource and multiple Connected Cache cache nodes:

# [PowerShell](#tab/powershell)

```powershell
#Define variables
$mccResourceName = "myMCCResource"
$cacheNodeName = "demo-node"
$cacheNodeOperatingSystem = "Windows"
$resourceGroup = "myRG"
$resourceLocation = "westus"
$cacheNodesToCreate = 2
$proxyHost = "myProxy.com"
$proxyPort = "8080"
$waitTime = 3

# Create Microsoft Connected Cache Azure resource
az mcc ent resource create --mcc-resource-name $mccResourceName --location $resourceLocation --resource-group $resourceGroup

#Loop through $cacheNodesToCreate iterations
for ($cacheNodeNumber = 1; $cacheNodeNumber -le $cacheNodesToCreate; $cacheNodeNumber++) {
    $iteratedCacheNodeName = $cacheNodeName + "-" + $cacheNodeNumber

    #Create cache node
    az mcc ent node create --cache-node-name $iteratedCacheNodeName --mcc-resource-name $mccResourceName --host-os $cacheNodeOperatingSystem --resource-group $resourceGroup

    #Get cache node state
    $cacheNodeState = $(az mcc ent node show --cache-node-name $iteratedCacheNodeName --mcc-resource-name $mccResourceName --resource-group $resourceGroup --query "cacheNodeState") | ConvertFrom-Json

    $howLong = 0
    #Wait until cache node state returns "Not Configured"
    while ($cacheNodeState -ne "Not Configured") {
        Write-Output "Waiting for cache node creation to complete...$howLong seconds"
        Start-Sleep -Seconds $waitTime
        $howLong += $waitTime

        $cacheNodeState = $(az mcc ent node show --cache-node-name $iteratedCacheNodeName --mcc-resource-name $mccResourceName --resource-group $resourceGroup --query "cacheNodeState") | ConvertFrom-Json
    }

    #Configure cache node
    az mcc ent node update --cache-node-name $iteratedCacheNodeName --mcc-resource-name $mccResourceName --resource-group $resourceGroup --cache-drive  "[{physical-path:/var/mcc,size-in-gb:50}]" --proxy enabled --proxy-host $proxyHost --proxy-port $proxyPort
}
```
