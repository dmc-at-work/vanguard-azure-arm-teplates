### README ###

How to run

# FORMAT
```
$ az group deployment create \
  --name {{deployment-name}} \
  --resource-group {{resource-group-name}} \
  --template-file deploy.json \
  --parameters storageAccountName={{storage-account-name}} location={{location}} accountType={{account-type}} kind={{kind}} supportsHttpsTrafficOnly=true accessTier={{access-tier}}
```

# SAMPLE
```
$ az group deployment create \
  --name StorageAccountDeployment \
  --resource-group sci-rg-development \
  --template-file deploy.json \
  --parameters storageAccountName=sadevelopment location=southeastasia accountType=Standard_LRS kind=Storage supportsHttpsTrafficOnly=true
```
