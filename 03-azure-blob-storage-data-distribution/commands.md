These commands assume you are creating a resource group of `az-redundancy-cli-demo-rg`.

And two Storage Accounts. One named `azclidemolrs` and one named `azclidemogzrs`.

Remember to replace the values with the values you are using in your Azure Account.

Create the Resource Group:

```
az group create \
  --name az-redundancy-cli-demo-rg \
  --location westus2 \
  --only-show-errors
```

Create the Storage Accounts (Each command can take ~20 seconds):
  
```
az storage account create \
  --name lrsacctdemo \
  --resource-group az-redundancy-cli-demo-rg \
  --location westus2 \
  --sku Standard_LRS \
  --kind StorageV2 \
  --access-tier Hot \
  --only-show-errors
```

```
az storage account create \
  --name gzrsacctdemo \
  --resource-group az-redundancy-cli-demo-rg \
  --location westus2 \
  --sku Standard_GZRS \
  --kind StorageV2 \
  --access-tier Hot \
  --only-show-errors
```
