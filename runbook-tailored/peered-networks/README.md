### README - runbook-tailred > peered-networks ###

Resources provisioned by this template:
* 2 Virtual network
* 1 Peering configuration

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
  --name PeeredNetworks \
  --resource-group rg-development \
  --template-file deploy.json \
  --parameters \
  vnetNameA=vn-development-web-001 \
  locationA=southeastasia \
  addressPrefixA=10.10.0.0/24 \
  subnetNameA=sn-development-web-001 \
  subnetAddressPrefixA=10.10.0.0/26 \
  enableDdosProtectionA=false \
  vnetNameB=vn-development-api-001 \
  locationB=southeastasia \
  addressPrefixB=10.20.0.0/24 \
  subnetNameB=sn-development-api-001 \
  subnetAddressPrefixB=10.20.0.0/26 \
  enableDdosProtectionB=false

# No Parameters
$ az group deployment create \
  --name PeeredNetworks \
  --resource-group rg-development \
  --template-file deploy.json
```

# CLEANUP
Note that this does not remove the resources, namely the virtual networks. It is reccommended to remove the resource group and all it's resources.
```
# FORMAT
$ az group deployment delete --name {{deployment-name}} --resource-group={{resource-group}}

# SAMPLE
$ az group deployment delete --name PeeredNetworks --resource-group=rg-development

```