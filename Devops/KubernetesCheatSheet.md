# Kubernetes Cheat Sheet

## Namespaces

### List namespaces

```
kubectl get namespace
```

* **default** The default namespace for objects with no other namespace
* **kube-system** The namespace for objects created by the Kubernetes system
* **kube-public** This namespace is created automatically and is readable by all users (including those not
  authenticated). This namespace is mostly reserved for cluster usage, in case that some resources should be visible and
  readable publicly throughout the whole cluster. The public aspect of this namespace is only a convention, not a
  requirement.

### Setting the namespace preference

You can permanently save the namespace for all subsequent kubectl commands in that context.

```
kubectl config set-context --current --namespace=<insert-namespace-name-here>
# Validate it
kubectl config view | grep namespace:
```

### Items not in namespace

```
# In a namespace
kubectl api-resources --namespaced=true

# Not in a namespace
kubectl api-resources --namespaced=false
```

## ReplicaSet

```
kubectl describe rs/frontend
```
