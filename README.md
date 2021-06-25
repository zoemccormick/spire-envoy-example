# spire-envoy-example

This repo provides a simple setup of SPIRE for Kubernetes, and two Envoy proxy deployments to communicate to each other using SPIFFE mTLS.

For a quickstart follow this README.

## Prerequisites

1. A running Kubernetes cluster.

## Install

1. Install the SPIRE server and agent.

```bash
kubectl apply -f spire/server_template.yaml
```

Wait for the spire server pod to come up with `2/2` containers with `kubectl get pods -n spire -w`.

Once it is up, install the agent:

```bash
kubectl apply -f spire/agent_template.yaml
```

2. Install the envoy ingress proxy and envoy backend service deployments. The images are for the `Dockerfile`'s found in `/services` are already generated and tagged at `zoemccormick/spire-envoy-example:ingress` and `zoemccormick/spire-envoy-example:backend`, respectively.

```bash
kubectl apply -f services/edge-deployment.yaml
kubectl apply -f services/backend-deployment.yaml
```

## updating the deployments

If you want to update the envoy configurations and try new images, make the changes and build with:

```bash
docker build -f services/edge-proxy/Dockerfile .
```
