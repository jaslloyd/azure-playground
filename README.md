# Azure Blob Storage Playground

## Azure Commands

View account Data: `az account list`
Output:
```
[
  {
    "cloudName": "AzureCloud",
    "homeTenantId": "ID_HERE",
    "id": "UNIQUE_ID",
    "isDefault": true,
    "managedByTenants": [],
    "name": "Free Trial",
    "state": "Enabled",
    "tenantId": "ID_HERE",
    "user": {
      "name": "EMAIL",
      "type": "user"
    }
  }
]
```

A resource group is a logical container into which Azure resources are deployed and managed.
View resource groups: `az group list`
Output:
```
[
  {
    "id": "/subscriptions/ACCOUNT_UNIQUE_ID/resourceGroups/static-test",
    "location": "northeurope",
    "managedBy": null,
    "name": "static-test",
    "properties": {
      "provisioningState": "Succeeded"
    },
    "tags": null,
    "type": "Microsoft.Resources/resourceGroups"
  }
]
```

A storage account goes in a resource group. The general-purpose storage account can be used for all four services: blobs, files, tables, and queues.
View Storage account Keys: `az storage account keys list --account-name ACCOUNT_NAME`
Output:
```
[
  {
    "keyName": "key1",
    "permissions": "Full",
    "value": "KEY_HERE"
  },
  {
    "keyName": "key2",
    "permissions": "Full",
    "value": "KEY_HERE"
  }
]
```

## Blob storage (will need env variables setup)
Blobs are  object storage for unstructured data via command line help [here](https://docs.microsoft.com/en-us/cli/azure/storage/blob?view=azure-cli-latest#az-storage-blob-upload-batch)
Blobs are always uploaded into a container.
Create a container like so: `az storage container create --name sample-container`

Uploading to a blob via: `az storage blob upload --container-name sample-container --name package.json --file package.json`

Uploading a bunch of files via: `az storage blob upload-batch -d sample-container -s <path-to-directory>`

## Hosting a website on Azure Blob Storage
High level steps:
1. Create a resource group
2. Create a storage account resource in that group
3. Enable static website hosting under Under settings/Static Web.
4. Give it an index document name (e.g index.html) and error document if you want
5. Click save
6. Visit primary endpoint you are provided
7. Use below steps in Blob Storage section to upload static files to blog storage container.

Follow along with Quick start guide [here](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-cli)
