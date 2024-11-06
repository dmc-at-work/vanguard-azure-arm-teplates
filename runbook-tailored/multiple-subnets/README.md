### README - runbook-tailred > multiple-subnets ###

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
  --name MultipleSubnets \
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
  enableDdosProtection=false

# No Parameters
$ az group deployment create \
  --name PeeredNetworks \
  --resource-group rg-development \
  --template-file deploy.json
```