# Publish our blog

Now that we've deployed our Cartographer Supply Chain and its various
components, it's time to (finally!) deploy our Workload and publish
blog.carlosnunez.me!

## Deploy the blog.carlosnunez.me Workload

First, we'll create a `Workload` that will publish blog.carlosnunez.me:

```sh
kubectl apply -f blogs/blog.carlosnunez.me/workload.yaml \
    -n blog
```
