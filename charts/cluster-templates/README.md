# Rancher Cluster Templates Helm Chart

|    Type     | Chart Version | App Version |
| :---------: | :-----------: | :---------: |
| application |    `0.7.1`    |   `0.7.1`   |

⚠️ This project is still in active development. As we continued to develop it, there will be breaking changes. ⚠️

## Supported Providers

### Currently Available

- AWS Commercial
- AWS GovCloud
- Harvester
- Digital Ocean
- VMWare vSphere
- Custom

### Pending Validation

- Microsoft Azure

## Installing the Chart

### Helm Install via Repository

```bash
helm repo add cluster-templates https://rancherfederal.github.io/rancher-cluster-templates
helm upgrade -i cluster cluster-templates/rancher-cluster-templates -n fleet-default -f values.yaml
```

## Helm Install via Registry
```bash
helm upgrade -i cluster oci://ghcr.io/rancherfederal/charts/rancher-cluster-templates -n fleet-default -f values.yaml
```

## Helm Chart Deployment Status

```bash
helm status cluster -n fleet-default
```

## Uninstalling the Chart

```bash
helm delete cluster -n fleet-default
```

## Chart/Cluster Secrets Management

### Cloud Credentials

If you do not have Cloud Credentials already created within the Rancher Manager, you can create them via `kubectl` with the command(s) below. Eventually, we will be moving these options with the Helm Chart!

#### For AWS Credentials

```bash
# with long-term credentials (accessKey and secretKey)
kubectl create secret -n cattle-global-data generic aws-creds-sts --from-literal=amazonec2credentialConfig-defaultRegion=$REGION --from-literal=amazonec2credentialConfig-accessKey=$ACCESSKEY --from-literal=amazonec2credentialConfig-secretKey=$SECRETKEY

kubectl annotate secret -n cattle-global-data aws-creds provisioning.cattle.io/driver=aws
```

```bash
# with temporary credentials (accessKey, secretKey, sessionToken)
kubectl create secret -n cattle-global-data generic aws-creds --from-literal=amazonec2credentialConfig-defaultRegion=$REGION --from-literal=amazonec2credentialConfig-accessKey=$ACCESSKEY --from-literal=amazonec2credentialConfig-secretKey=$SECRETKEY --from-literal=amazonec2credentialConfig-sessonToken=$SESSIONTOKEN

kubectl annotate secret -n cattle-global-data aws-creds provisioning.cattle.io/driver=aws
```

#### For Harvester Credentials

```bash
export CLUSTERID=$(kubectl get clusters.management.cattle.io -o=jsonpath='{range .items[?(@.metadata.labels.provider\.cattle\.io=="harvester")]}{.metadata.name}{"\n"}{end}')

kubectl create secret -n cattle-global-data generic harvester-creds --from-literal=harvestercredentialConfig-clusterId=$CLUSTERID --from-literal=harvestercredentialConfig-clusterType=imported --from-file=harvestercredentialConfig-kubeconfigContent=harvester.yaml

kubectl annotate secret -n cattle-global-data harvester-creds provisioning.cattle.io/driver=harvester
```

#### For Digital Ocean Credentials

```bash
kubectl create secret -n cattle-global-data generic digitalocean-creds --from-literal=digitaloceancredentialConfig-accessToken=$TOKEN

kubectl annotate secret -n cattle-global-data digitalocean-creds provisioning.cattle.io/driver=digitalocean
```


#### For VMWare vSphere Credentials

```bash
kubectl create secret -n cattle-global-data generic vsphere-creds --from-literal=vmwarevspherecredentialConfig-username=$USERNAME --from-literal=vmwarevspherecredentialConfig-password=$PASSWORD --from-literal=vmwarevspherecredentialConfig-vcenter=$VCENTER_HOST --from-literal=vmwarevspherecredentialConfig-vcenterPort=$VCENTER_PORT

kubectl annotate secret -n cattle-global-data vsphere-creds provisioning.cattle.io/driver=vmwarevsphere
```

### Registry Credentials

If you are configuring an authenticated registry and do not have Registry Credentials created in the Rancher Manager, you can create them via `kubectl` with the command below:

```bash
kubectl create secret -n fleet-default generic --type kubernetes.io/basic-auth registry-creds --from-literal=username=USERNAME --from-literal=password=PASSWORD
```
