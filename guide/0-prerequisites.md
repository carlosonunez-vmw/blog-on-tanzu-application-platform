# Prerequisites

Make sure that you have these on your machine.

## Common

- A Docker Hub account (to push images into)

## Local

- An Intel machine (because Cartographer does not support ARM.
  [#791](https://github.com/vmware-tanzu/cartographer/issues/791)
- [Kind](https://kind.sigs.k8s.io) using Kubernetes v1.24 or later.
- Docker or containerd.

## Remote

Any Kubernetes cluster with at least one `amd64` node should work, like
EKS, AKS, GKE, etc.
