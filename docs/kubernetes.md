# Kubernetes Cheat Sheet

## Resource guide

### Nodes

### Pods

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

### ConfigMap

### Deployments

### Services

```bash
# see all services in all namespaces
kubectl get services -A
```

### Ingress

```bash
# see all ingresses in all namespaces
kubectl get ingress -A

# see a resource definition
kubectl get ingress mymicroservice -o yaml
```

## Service provider

### Azure Kubernetes Service (AKS)

```bash
# review agent pool specification
az aks show --resource-group myrgname --name myaksname --query agentPoolProfiles

# scale agent pool (2 nodes here)
az aks scale --resource-group myrgname --name myaksname --node-count 2 --query properties.provisioningState
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
