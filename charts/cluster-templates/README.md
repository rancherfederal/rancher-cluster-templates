# Rancher Cluster Templates Helm Chart

|  Type   | Chart Version | App Version |
| :-----: | :-----------: | :---------: |
| library |   `v0.2.0`    |  `v0.2.0`   |

## Important Notes

### Verified and Tested Providers:

- AWS Commercial
- AWS GovCloud
- Rancher Harvester
- VMWare vSphere

## Installing the Chart

```bash
helm repo add cluster-templates https://rancherfederal.github.io/rancher-cluster-templates
helm upgrade -i cluster cluster-templates/rancher-cluster-templates -n fleet-default -f values.yaml
```

```bash
helm status cluster -n fleet-default
```

## Uninstalling the Chart

```bash
helm delete cluster -n fleet-default
```

## Example Configurations

- [Amazon EC2](values-aws.yaml)
  - [Example](../../examples/aws/values-aws.yaml)
- [Microsoft Azure](values-azure.yaml)
- [Digital Ocean](values-do.yaml)
- [Rancher Harvester](values-harvester.yaml)
- [VMWare vSphere](values-vsphere.yaml)
