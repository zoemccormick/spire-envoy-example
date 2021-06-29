# spire-envoy-example

This guide was created for a blog post which can be found [here](https://zoemccormick.medium.com/getting-started-with-envoy-spiffe-and-kubernetes-32f34cda5f35).

This repo provides a simple setup of SPIRE for Kubernetes, and two Envoy proxy deployments to communicate to each other using SPIFFE mTLS.

## A note on updating the deployments

If you want to update the envoy configurations and try new images, make the changes and build with:

```bash
cd services/edge-proxy
docker build .
```

or

```bash
cd services/hello-world
docker build .
```
