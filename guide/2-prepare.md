# Prepare a Namespace for Blog Workloads

In this section, we'll create a namespace that will hold `Workloads` that
define the blogs that we want to deploy.

These `Workloads` will turn a Git repository holding a blog into a blog that
we can access online.

## Create our "dev namespace"

First, we will create a namespace to hold our Tekton `Pipeline` inside of.
We'll call this a "dev namespace" for the rest of this guide.

```sh
kubectl create ns blog
```

Afterwards, make the default Service Account in the namespace an admin
in the cluster.

```sh
kubectl apply -f resources/namespace/role.yaml
```

> ⚠️  This is against best-practices and is not recommended. We're only
> doing this here for testing.

## Provision a Docker Hub Registry Secret

Afterwards, create a Docker Registry `Secret` called `blog-secret`
within this namespace to store your Docker Hub credentials inside of.

```sh
kubectl create secret docker-registry blog-secret \
    --docker-username=$DOCKER_HUB_USERNAME \
    --docker-password=$DOCKER_HUB_PASSWORD
```

