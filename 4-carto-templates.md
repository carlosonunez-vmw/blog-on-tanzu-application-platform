# Deploy the Cartographer Cluster Templates

Now that we have our Tekton pipeline, let's deploy the Cluster Templates that
are used by our Supply Chain to accept our Workload and ship our blog.

```sh
kubectl apply -f blog_initializer_cct.yaml
kubectl apply -f blog_renderer_cit.yaml
```

This will create:

- A `ClusterConfigTemplate` that will validate the parameters supplied by the
  `Workload` we'll create and create a `ConfigMap` that will be used throughout
  the Supply Chain, and
- A `ClusterImageTemplate` that will turn the blog in our `Workload` into
  a container image that we'll create a `Deployment` with.


