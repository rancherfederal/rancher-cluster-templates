# Rancher Cluster Templates Helm Chart

|  Type   | Chart Version | App Version |
| :-----: | :-----------: | :---------: |
| library |   `v0.1.0`    |  `v0.1.0`   |

## Requirements and Prerequsites

Required `values.yaml` Variables:

- VPC ID (`vpcId`)
- Subnet ID (`subnetId`)
- IAM Instance Profile (`iamInstanceProfile`)
- Provider Cloud Credentials (`cloudCredentialSecretName`)

Verified and Tested:

- AWS Commercial
- AWS GovCloud
- Rancher Harvester
- VMWare vSphere

## Installing the Chart

```bash
helm repo add cluster-templates https://rancherfederal.github.io/rancher-cluster-templates
helm install cluster cluster-templates/rancher-cluster-templates -n fleet-default -f values.yaml
```

```bash
helm status -n
```

## Uninstalling the Chart

```bash
helm uninstall -n
```

## Example Configurations

- [Amazon EC2](values-aws.yaml)
- [Microsoft Azure](values-azure.yaml)
- [Digital Ocean](values-do.yaml)
- [Rancher Harvester](values-harvester.yaml)
- [VMWare vSphere](values-vsphere.yaml)
