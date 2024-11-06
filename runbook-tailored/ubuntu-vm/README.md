### README - runbook-tailred > ubuntu-vm ###

Will provision the following resources
* Virtual network
* Subnet
* IP Address
* Virtual machine
* Storage account (for diagnostic)

# Format
```
$ az group deployment create \
  --name {{deployment-name}} \
  --resource-group {{resource-group-name}} \
  --template-file deploy.json \
  --parameters 
```

# SAMPLE
```
$ az group deployment create \
  --name UbuntuVM \
  --resource-group sci-rg-development \
  --template-file deploy.json \
  --parameters \
  virtualNetworkName=vn-development \
  location=southeastasia \
  addressPrefix=10.0.0.0/16 \
  subnetName=sn-development-001 \
  subnetAddressPrefix=10.0.0.0/24 \
  enableDdosProtection=false \
  publicIPAddressName=ipbastion \
  dnsLabelPrefix=zodevelopment \
  networkInterfaceName=vm-geek-test-00001708 \
  networkSecurityGroupName=vm-geek-test-00001-nsg \
  virtualMachineName=vm-development-001 \
  osDiskType=Standard_LRS \
  virtualMachineSize=Standard_D2s_v3 \
  adminUsername=devops \
  adminPublicKey="ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC+/rXRO5vjU+6NzFwMmtMhZLL5IZ8ipeQN3Vphrz76Y13nSXXU2o3wK4BGoCogSygNP+IHpYQgaovAoD/qyvYsjPyv2cNlchrk0m3YDvWvTBf4Ox3N5+zf5M64P3XNwxdZkqwQCmzkSd0HT47YqvEGeacat4oUNwo7G5Zp1Ux4UV0fZgvXhGf51PX8jHQiGt1fToWY9xjGwEA9BPycYHU04fTqCUyAgOQUzgIsYQ3vJIneEFL3Scmxm4ptDCwmZV9P2NkLl8YlXzUDTyS9tESPTC/3w5LvLIDc0yDWZQFFCabXrR4/xBH8EHgZhP0vEqMZF4dIiWTIRfDUZkGIlaU3 john-reese" \
  diagnosticsStorageAccountName=rggeektestdiag \
  diagnosticsStorageAccountId=Microsoft.Storage/storageAccounts/rggeektestdiag \
  diagnosticsStorageAccountType=Standard_LRS diagnosticsStorageAccountKind=Storage
```

# SAMPLE - Template URI
```
$ az group deployment create \
  --name UbuntuVM \
  --resource-group sci-rg-development \
  --template-uri https://bitbucket.org/zedoptima-vanguard/azure-arm-templates/src/development/runbook-tailored/ubuntu-vm/deploy.json \
  --parameters ...
```