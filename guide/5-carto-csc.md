# Deploy the Supply Chain

Now that we have all of the pieces in order, let's deploy our
Supply Chain:

```sh
kubectl apply -f supply_chain.yaml
```

This will create a `SupplyChain` called `publish-blog` that links
all of the pieces we created above together.

Let's describe it and make sure that it's in a `Ready` state.

```sh
kubectl describe csc publish-blog
```

You should get output similar to the below:

```text
$: kubectl describe csc publish-blog
Name:         publish-blog
Namespace:
Labels:       <none>
Annotations:  <none>
API Version:  carto.run/v1alpha1
Kind:         ClusterSupplyChain
Metadata:
  Creation Timestamp:  2023-10-13T15:59:04Z
  Generation:          2
  Resource Version:    42796926
  UID:                 45efcdd1-3fea-4b2b-956f-e1098c9bc623
Spec:
  Params:
    Name:   default_blog_gen_url
    Value:  http://github.com/carlosonunez/https-hugo-bloggen
    Name:   default_blog_gen_version
    Value:  v2.2.1
    Name:   default_blog_gen_registry
    Value:  docker.io
    Name:   default_blog_gen_registry_secret
    Value:  blog-repo-secret
  Resources:
    Name:  config
    Template Ref:
      Kind:  ClusterConfigTemplate
      Name:  blog-config
    Configs:
      Name:      blog-config
      Resource:  config
    Name:        image
    Template Ref:
      Kind:  ClusterImageTemplate
      Name:  blog-renderer
  Selector:
    Is - Blog:  true
Status:
  Conditions:
    Last Transition Time:  2023-10-13T16:01:02Z
    Message:
    Reason:                Ready
    Status:                True
    Type:                  TemplatesReady
    Last Transition Time:  2023-10-13T16:01:02Z
    Message:
    Reason:                Ready
    Status:                True
    Type:                  Ready
  Observed Generation:     2
Events:                    <none>
```

