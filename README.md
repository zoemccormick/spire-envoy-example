# spire-envoy-example

[To deploy - ](https://blog.markvincze.com/how-to-use-envoy-as-a-load-balancer-in-kubernetes/)

This repo was created for a blog post - [TODO link blog post]. To see an explanation of the deployments check it out.

For a quickstart - follow this README.

## Prerequisites

1. A running Kubernetes cluster.
2. Ladeeda.

## Install

1. Install the SPIRE server and agent.

```bash
kubectl create ns spire
kubectl apply -f spire/server_template.yaml
```

Wait for the spire server pod to come up with `2/2` containers with `kubectl get pods -n spire -w`.

Once it is up, install the agent:

```bash
kubectl apply -f spire/agent_template.yaml
```

2. Install the envoy ingress proxy and envoy backend service deployments. The images are for the `Dockerfile`'s found in `/services` are already generated and tagged at `zoemccormick/spire-envoy-example:ingress` and `zoemccormick/spire-envoy-example:backend`, respectively.

```bash
kubectl apply -f services/ingress-svc.yaml
kubectl apply -f services/ingress-deployment.yaml
kubectl apply -f services/backend-deployment.yaml
```
