# Istio Service Mesh

Istio is a service mesh for Kubernetes

## What is a Service Mesh?

A service mesh is a dedicated infrastructure layer that you can add to your applications.

Istio Service Mesh helps us add observability, manage traffic, and add secure our workloads.

Istio "SideCars" are attached to every pod running in a namespace labeled for Istio injection.

This side car will intercept and proxy all traffic to and from the pod it is attached to.