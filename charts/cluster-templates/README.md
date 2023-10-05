# Cluster Templates Helm Chart

| Type | Chart Version | App Version |
| :--: | :-----------: | :---------: |
| app  | `v0.0.1` | `v0.0.1` |

## Installing the Chart
```bash
helm install -n
```
```bash
helm status -n
```

## Uninstalling the Chart
```bash
helm uninstall -n
```

## Example Configurations
* [Amazon EC2](values-aws.yaml)
* [Microsoft Azure](values-azure.yaml)
* [Digital Ocean](values-do.yaml)
* [Rancher Harvester](values-harvester.yaml)
* [VMWare vSphere](values-vsphere.yaml)