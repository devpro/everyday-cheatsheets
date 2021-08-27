# Kubectl (Kubernetes CLI) Cheat Sheet

## Documentation

- [Overview](https://kubernetes.io/docs/reference/kubectl/overview/)
- [Installation](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Cheatsheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
- [Source code](https://github.com/kubernetes/kubernetes/tree/master/pkg/kubectl)

## Local configuration

`~/.kube/config` is the local configuration file (contains all the contexts, information about the clusters and user credentials)

```bash
# get current context
kubectl config current-context

# display context configuration
kubectl config get-contexts

# change context
kubectl config use-context <cluster-name>
```

## Cluster information

```bash
# display version
kubectl version

# display cluster information
kubectl cluster-info

# display cluster configuration
kubectl config get-clusters

# get health information for the control plane components (the scheduler, the controller manager and etcd)
kubectl get componentstatuses

# list all the nodes in the cluster and report their status and Kubernetes version
kubectl get nodes

# show the CPU and memory capacity of each node, and how much of each is currently in use
kubectl top pods

# view sereval resources at once
kubectl get deploy,rs,po,svc,ep
```

## Management

```bash
# create resources from a manifest file
kubectl create -f <filename>

# create or update resources from a manifest file
kubectl update -f <filename>

# delete resources from a manifest file
kubectl delete -f <filename>
```

## Objects

### Namespaces (ns)

```bash
# list all namespaces
kubectl get namespaces

# create a new namespace
kubectl create ns hello-there
```

### Pods

```bash
# list pods of a specific namespace
kubectl get pods --namespace kube-system

# list pods of all namespaces
kubectl get pods -A

# get more information about a pod
kubectl describe pod

# get log information of a specific pod
kubectl logs

# get pod yaml definition
kubectl get pod -o yaml

# watch pods
watch kubectl get pod --all-namespaces

# desribe a pod
kubectl describe pod <pod-name> --namespace <namespace>

# get pod logs
kubectl logs [--tail=20] [--since=1h] <pod-name>

# display metrics about a pod and its containers
kubectl top pod <pod-name> --containers

# execute commands inside a pod (for investigation purpose)
kubectl exec -it <pod-name> -n <namespace> -- /bin/bash

# download or upload files from a container
kubectl cp my-file.txt <namespace>/<pod-name>:my-file.txt
kubectl cp <namespace>/<pod-name>:my-file.txt my-file.txt
```

### ServiceAccounts

```bash
# see all service accounts in all namespaces
kubectl get ServiceAccount -A
```

### Definitions

#### CustomResourceDefinition

### RBAC

#### ClusterRole

#### ClusterRoleBinding

#### Role

#### RoleBinding

### MutatingWebhookConfiguration

### ValidatingWebhookConfiguration

### Secrets

```bash
# see all secrets in all namespaces
kubectl get secrets -A
```

### CronJobs (cj)

```bash
# create a CronJob
kubectl create cronjob my-cron --image=busybox --schedule="*/5 * * * *" -- echo hello

# update a CronJob
kubectl edit cronjob/my-cron

# update a CronJob with a specific IDE
KUBE_EDITOR="nano" kubectl edit cronjob/my-cron

# delete a CronJob
kubectl delete cronjob my-cron
```

### ConfigMap

### Deployments

```bash
kubectl get deployment
```

### Services

```bash
# see all services in all namespaces
kubectl get services -A
```

### Events

```bash
kubectl get events --sort-by=.metadata.creationTimestamp
```

### Ingress

```bash
# see all ingresses in all namespaces
kubectl get ingress -A

# see a resource definition
kubectl get ingress mymicroservice -o yaml
```

## Actions

### Scale

```bash
kubectl scale
```

## Port forwarding

```bash
kubectl port-forward xxx 8080:80
```

## Proxy

```bash
# runs a proxy to the Kubernetes API Server
kubectl proxy
```

## Service provider

### Azure Kubernetes Service (AKS)

```bash
# review agent pool specification
az aks show --resource-group myrgname --name myaksname --query agentPoolProfiles

# scale agent pool (2 nodes here)
az aks scale --resource-group myrgname --name myaksname --node-count 2 --query properties.provisioningState
```

### Google Kubernetes Engine (GKE)

```bash
gcloud container clusters create mycluster

gcloud container clusters list

kubectl get nodes

gcloud container clusters delete linuxfoundation
```

## Recipes

### Quick fixes

```bash
# find and delete pods
kubectl delete pods $(kubectl get pods -o=name | grep mypodname | sed "s/^.\{4\}//")
```

### Known issues

Issue | Advice
----- | ------
Pod with status `CreateContainerConfigError` | Look at the pod logs (`kubectl logs podxxx`), the issue should be detailed there
