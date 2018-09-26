# Ant crasher deployment

## Workstation Setup

Ensure you have the following tools installed:
* kubectl
* helm

Ensure you have the ac.fuse.tikal.io cluster context setup.

## Kubernetes Installation

See [./ac.fuse.tikal.io/](./ac.fuse.tikal.io/)

## Ant Crasher Deploy

Use helm command-line tool to deploy ant-crasher:

```sh
helm install ./helm/ant-umbrella
```
