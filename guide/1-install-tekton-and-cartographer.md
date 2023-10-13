## Create Infrastructure

In this section, we'll install Cartographer and `cert-manager`, a
Kubernetes-native certificate provisioning service.

We'll also install Tekton Pipelines, a Kubernetes-native build runner. While you
don't need to use Tekton with Cartographer, describing the multiple steps
involved in deploying this blog (or any Hugo-based blog) is much easier to do
with Tekton than raw Kubernetes.

### Installing Cert Manager

Install Cert Manager `v1.13.1`:

```sh
kubectl apply -f \
    https://github.com/cert-manager/cert-manager/releases/download/v1.13.1/cert-manager.yaml
```

Then make sure that its `Pod`s are in a healthy state:

```sh
kubectl get pods -n cert-manager
```

You should see something like this:

```text
NAME                                      READY   STATUS    RESTARTS   AGE
cert-manager-69c6698f48-xzvtx             1/1     Running   0          4d4h
cert-manager-cainjector-68ccb8b45-f4br2   1/1     Running   0          18h
cert-manager-webhook-745bf8c94f-2xrm5     1/1     Running   0          18h
```

### Installing Cartographer

Install Cartographer:

```sh
kubectl apply -f \
    https://github.com/vmware-tanzu/cartographer/releases/download/v0.8.2/cartographer.yaml
```

Then, like Cert Manager, make sure that its `Pod`s are in a healthy state:

```sh
kubectl get pods -n cartographer-system
```

You should see something like this:

```text
NAME                                                          READY   STATUS    RESTARTS   AGE
cartographer-controller-6bf945848c-jd556                      1/1     Running   0          18h
cartographer-conventions-controller-manager-7cc66bb6c-pvw6t   1/1     Running   0          4d4h
```

### Installing Tekton

Install the latest version of Tekton:

```sh
kubectl apply \
    -f https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
```

Then, like Cartographer and Cert Manager, make sure everything's healthy:

```sh
kubectl get pods -n tekton-pipelines
```

Output:

```sh
NAME                                          READY   STATUS    RESTARTS   AGE
tekton-pipelines-controller-94df4d884-btbfb   1/1     Running   0          3d17h
tekton-pipelines-webhook-59578bf6bb-rr5dm     1/1     Running   0          28h
```
