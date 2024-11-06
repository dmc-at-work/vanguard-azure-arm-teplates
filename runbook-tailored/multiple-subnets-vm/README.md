### README - runbook-tailred > multiple-subnets-vm ###

Resources provisioned by this template:
* 1 Virtual network
* 4 subnets (1 each for bastion, web, app and data)

# FORMAT
```
$ az group deployment create \
  --name {{deployment-name}} \
  --resource-group {{resource-group-name}} \
  --template-file deploy.json \
  --parameters 
```

# SAMPLE
```
# With sample parameters
$ az group deployment create \
  --name MultipleSubnetsVM \
  --resource-group rg-development \
  --template-file deploy.json \
  --parameters \
  vnetName=vn-development-001 \
  location=southeastasia \
  addressPrefix=10.10.0.0/16 \
  subnetNameA=sn-development-bastion \
  subnetAddressPrefixA=10.10.0.0/24 \
  subnetNameB=sn-development-web \
  subnetAddressPrefixB=10.10.10.0/24 \
  subnetNameC=sn-development-app \
  subnetAddressPrefixC=10.10.20.0/24 \
  subnetNameD=sn-development-data \
  subnetAddressPrefixD=10.10.30.0/24 \
  enableDdosProtection=false \
  publicIpAddressNameA=ipbastion \
  dnsLabelPrefixA=zodevelopment \
  networkInterfaceNameA=ni-dev-mgmt-00001708 \
  networkSecurityGroupNameA=ni-dev-mgmt-001-nsg \
  virtualMachineNameA=vm-development-001 \
  osDiskTypeA=Standard_LRS \
  virtualMachineSizeA=Standard_D2s_v3 \
  adminUsernameA=devops \
  diagnosticsStorageAccountName=rggeektestdiag \
  diagnosticsStorageAccountId=Microsoft.Storage/storageAccounts/rggeektestdiag \
  diagnosticsStorageAccountType=Standard_LRS \
  diagnosticsStorageAccountKind=Storage

# No Parameters
$ az group deployment create \
  --name PeeredNetworks \
  --resource-group rg-development \
  --template-file deploy.json
```

Enter the SSH public key when asked
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC+/rXRO5vjU+6NzFwMmtMhZLL5IZ8ipeQN3Vphrz76Y13nSXXU2o3wK4BGoCogSygNP+IHpYQgaovAoD/qyvYsjPyv2cNlchrk0m3YDvWvTBf4Ox3N5+zf5M64P3XNwxdZkqwQCmzkSd0HT47YqvEGeacat4oUNwo7G5Zp1Ux4UV0fZgvXhGf51PX8jHQiGt1fToWY9xjGwEA9BPycYHU04fTqCUyAgOQUzgIsYQ3vJIneEFL3Scmxm4ptDCwmZV9P2NkLl8YlXzUDTyS9tESPTC/3w5LvLIDc0yDWZQFFCabXrR4/xBH8EHgZhP0vEqMZF4dIiWTIRfDUZkGIlaU3 john-reese