# Rancher Cluster Templates Helm Chart

|  Type   | Chart Version |
| :-----: | :-----------: |
| library |   `v0.1.0`    |

## Installing the Chart

```bash
helm repo add cluster-templates https://rancherfederal.github.io/rancher-cluster-templates
helm install cluster cluster-templates/rancher-cluster-templates -n fleet-default -v values.yaml
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
