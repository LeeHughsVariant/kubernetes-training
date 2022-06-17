# Namespace

In Kubernetes, namespaces provides a mechanism for isolating groups of resources within a single cluster. Names of resources need to be unique within a namespace, but not across namespaces.

## Imperative Namespace Creation

```bash
kubectl create namespace my-namespace
```

## Declarative Namespace Creation

```bash
kubectl create -f namespace.yaml
```

## Set kube context to use your namespace

```bash
kubectl config set-context --current --namespace=my-namespace
```