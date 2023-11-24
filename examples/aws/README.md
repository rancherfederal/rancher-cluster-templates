### Required Variable Updates:

- Provider Cloud Credentials (`cloudCredentialSecretName`)
- VPC ID (`vpcId`)
- Subnet ID (`subnetId`)
- IAM Instance Profile (`iamInstanceProfile`)

## Installing the Chart

```bash
# fetch the values file (make sure to update variables)
curl -#OL https://raw.githubusercontent.com/rancherfederal/rancher-cluster-templates/main/examples/aws/values-aws.yaml
```

```bash
# add the helm chart
helm repo add cluster-templates https://rancherfederal.github.io/rancher-cluster-templates

# install the helm chart
helm upgrade -i cluster cluster-templates/rancher-cluster-templates -n fleet-default -f values-aws.yaml
```

```bash
# check the status of the helm chart
helm status cluster -n fleet-default
```

## Uninstalling the Chart

```bash
# uninstall the helm chart
helm delete cluster -n fleet-default
```
