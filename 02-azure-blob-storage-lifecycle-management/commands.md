These commands assume you are creating a resource group of `az-cli-demo-rg` a Storage Account named `azstoragescalingcli`. 

Remember to replace the values with the values you are using in your Azure Account.

Create the Resource Group:

```
az group create \
  --name az-cli-demo-rg \
  --location westus2 \
  --only-show-errors
```

Create the Storage Account (This command can take ~20 seconds):

```
az storage account create \
  --name azstoragescalingcli \
  --resource-group az-cli-demo-rg \
  --location westus2 \
  --sku Standard_LRS \
  --kind StorageV2 \
  --access-tier Hot \
  --only-show-errors
```

Set up Lifecycle Policies:

First make sure the lifecycle.json file is present. You can run `nano lifecycle.json` to open the file and then paste in the contents of lifecycle.json.

The running the following commands.

```
az storage account management-policy create \
  --account-name azstoragescalingcli \
  --resource-group az-cli-demo-rg \
  --policy @lifecycle.json
```

```
az storage account blob-service-properties update \
    --resource-group az-cli-demo-rg \
    --account-name azstoragescalingcli \
    --enable-last-access-tracking true
```

```
az storage account management-policy create \
  --account-name azstoragescalingcli \
  --resource-group az-cli-demo-rg \
  --policy @lifecycle.json
```
