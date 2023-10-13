# Deploy Tekton Pipeline

Next, we'll deploy the Tekton pipeline used by our Supply Chain that builds and
deploys our blog along with its requisite tasks.

```sh
kubectl apply -n blog -f resources/tekton/blog_renderer_pipeline.yaml
```

This will create four `ClusterTasks` that are referenced by
one `Pipeline` called `render-the-blog`.
