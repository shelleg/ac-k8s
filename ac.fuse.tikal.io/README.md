ac.fuse.tikal.io
================


## The following facts are assumed:

* A `kops` cluster name ac.fuze.tikal.io
* The `kops` state bucket  s3://ac.fuse.tikal.io
* An `aws` profile named kops-aws-tikal
* A `route53` zone preconfigured for `fuse.tikal.io`
* The `kops` public key is part of the repo you could get the private

## Connection to the cluster considering you have the above prequisites:

```
source setenv.sh      # sets the above Environment Variables
kops export kubecfg   # gets the kubernetes config file from s3 to ~/.kube/config
```
You should be able to run `kubectl cluster-info` - expect the following / similar output:

```
hagzag@🌀ac.fuse.tikal.io 👉  kubectl cluster-info
Kubernetes master is running at https://api.ac.fuze.tikal.io
KubeDNS is running at https://api.ac.fuze.tikal.io/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

## Creating the cluster via kops 1 liner ...

```
kops create cluster \
   --networking=weave \
   --ssh-public-key=./kops_rsa.pub \
   --master-count=1 \
   --master-size=t2.medium \
   --master-zones=eu-west-1b \
   --node-size=t2.large \
   --node-count=3 \
   --dns-zone=ZWGYCBG3RY9XT \
   --state=s3://ac.fuse.tikal.io \
   --topology=public \
   --cloud=aws \
   --associate-public-ip \
   --zones=eu-west-1a
```
