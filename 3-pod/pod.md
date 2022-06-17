# Pods

Pods are the smallest deployable units of computing that you can create and manage in Kubernetes.

A pod is a group of one or more containers with shared storage and network resources.

## Declarative Pod Creation

```bash
kubectl create -f pod.yaml
```

## Label Pods

```bash
kubectl label pod my-pod app=my-nginx
```

## Delete Pods

```bash
kubectl delete pod my-pod
```