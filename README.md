# Ant crasher deployment

## Workstation Setup

Ensure you have the following tools installed:

* kubectl
* helm

Ensure you have the ac.fuse.tikal.io cluster context setup.

Ensure you have the incubator helm repository set-up:

```sh
helm repo add incubator http://storage.googleapis.com/kubernetes-charts-incubator
```

## Kubernetes Installation

See [./ac.fuse.tikal.io/](./ac.fuse.tikal.io/)

## Ant Crasher Deploy

Use helm command-line tool to deploy ant-crasher:

```sh
kubectl create namespace ac
helm dep build ./helm/ant-umbrella
helm install --name ac --namespace ac ./helm/ant-umbrella
```

The `ant-umbrella` helm chart is an umbrella that deploys the following
sub-charts:

* [kafka](https://github.com/helm/charts/tree/master/incubator/kafka)
* [ant-firehose](./helm/ant-firehose/)
* [ant-publisher](./helm/ant-publisher/)
* [ant-ui](./helm/ant-ui/)
