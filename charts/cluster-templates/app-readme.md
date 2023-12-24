# Rancher Cluster Templates Helm Chart

|    Type     | Chart Version | App Version |
| :---------: | :-----------: | :---------: |
| application |   `v0.4.0`    |  `v0.4.0`   |

⚠️ This project is still in active development. As we continued to develop it, there will be breaking changes. ⚠️

## Supported Providers

### Currently Available

* AWS Commercial
* AWS GovCloud
* Harvester
* Custom

### Pending Development

* VMWare vSphere
* Microsoft Azure
* Digital Ocean

## Installing the Chart

```bash
helm repo add cluster-templates https://rancherfederal.github.io/rancher-cluster-templates
helm upgrade -i cluster cluster-templates/rancher-cluster-templates -n fleet-default -f values.yaml
```

```bash
helm upgrade -i cluster oci://ghcr.io/rancherfederal/rancher-cluster-templates -n fleet-default -f values.yaml
```

## Helm Chart Deployment Status

```bash
helm status cluster -n fleet-default
```

## Uninstalling the Chart

```bash
helm delete cluster -n fleet-default
```

## Example Configurations

* [Amazon EC2](https://github.com/rancherfederal/rancher-cluster-templates/blob/main/charts/cluster-templates/values-aws.yaml)
  * [Example Values](https://github.com/rancherfederal/rancher-cluster-templates/blob/main/examples/aws/values-aws.yaml)
  * [Example Values with Temporary Credentials](https://github.com/rancherfederal/rancher-cluster-templates/blob/main/examples/aws/values-aws-sts.yaml)
* [Custom](https://github.com/rancherfederal/rancher-cluster-templates/blob/main/charts/cluster-templates/values-custom.yaml)
  * [Example Values](https://github.com/rancherfederal/rancher-cluster-templates/blob/main/examples/custom/values-custom.yaml)
* [Harvester](https://github.com/rancherfederal/rancher-cluster-templates/blob/main/charts/cluster-templates/values-harvester.yaml)
  * [Example Values](https://github.com/rancherfederal/rancher-cluster-templates/blob/main/examples/harvester/values-harvester.yaml)
* VMWare vSphere (TBD)
* Microsoft Azure (TBD)
* Digital Ocean (TBD)

## Chart/Cluster Secrets Management

### Cloud Credentials

If you do not have Cloud Credentials created in the Rancher Manager, you can create them via `kubectl` with the command below.

#### For AWS Credentials

```bash
kubectl create secret -n cattle-global-data generic aws-creds --from-literal=amazonec2credentialConfig-defaultRegion=REGION --from-literal=amazonec2credentialConfig-accessKey=ACCESSKEY --from-literal=amazonec2credentialConfig-secretKey=SECRETKEY

kubectl annotate secret -n cattle-global-data aws-creds provisioning.cattle.io/driver=aws
```

#### For Harvester Credentials

```bash
coming soon...
```

### Registry Credentials

If you are configuring an authenticated registry and do not have Registry Credentials created in the Rancher Manager, you can create them via `kubectl` with the command below:

```bash
kubectl create secret -n fleet-default generic --type kubernetes.io/basic-auth registry-creds --from-literal=username=USERNAME --from-literal=password=PASSWORD
```
