# Azure Kubernetes Service (AKS)

[docs.microsoft.com/azure/aks](https://docs.microsoft.com/en-us/azure/aks/intro-kubernetes)

## Concepts

### Cluster architecture

<img src="https://docs.microsoft.com/en-us/azure/aks/media/concepts-clusters-workloads/control-plane-and-nodes.png">

## Practice

### Course

- [Introduction to Azure Kubernetes Service](https://docs.microsoft.com/en-us/learn/modules/intro-to-azure-kubernetes-service/index?source=learn)

### Quickstart

- Microsoft [Deploy an Azure Kubernetes Service (AKS) cluster using the Azure portal](https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough-portal)

- Microsoft [Quickstart: Deploy an Azure Kubernetes Service cluster using the Azure CLI](https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough)

```bash
# Make sure Azure CLI is installed
az --version

# Get all available locations information
az account list-locations

# Create the resource group
az group create --name rg-quickstart-aks-payg-001 --location westeurope

# (optional) Create the service principal explicitely
az ad sp create-for-rbac --skip-assignment

# Create the ask instance
az aks create --resource-group rg-quickstart-aks-payg-001 --name aks-quickstart-payg-001 --node-vm-size Standard_B2s --node-count 1 --dns-name-prefix dns-aks-quickstart-payg-001 --enable-addons monitoring --generate-ssh-keys

# Grab cluster information
az aks get-credentials --resource-group rg-quickstart-aks-payg-001 --name aks-quickstart-payg-001

# Check cluster access is ok
kubectl get nodes

# Look at the pods
kubectl get pods

# Write the application definition file
code azure-vote.yaml

# Deploy the application
kubectl apply -f azure-vote.yaml

# Monitor the deployment (it will also indicate the external ip address that you use to access the voting web app from your browser)
kubectl get service azure-vote-front --watch

# Review back service status
kubectl get service azure-vote-back

# Get cluster information
kubectl cluster-info

# Get performance info on the top node
kubectl top node

# Add the role to access the dashboard
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard

# Start the Kubernetes dashboard
az aks browse --resource-group rg-quickstart-aks-payg-001 --name aks-quickstart-payg-001

# Look at existing upgrades
az aks get-upgrades --resource-group rg-quickstart-aks-payg-001 --name aks-quickstart-payg-001

# Do the upgrade
az aks upgrade --resource-group rg-quickstart-aks-payg-001 --name aks-quickstart-payg-001 --kubernetes-version 1.14.6

# Get cluster info
az aks show --resource-group rg-quickstart-aks-payg-001 --name aks-quickstart-payg-001 --output table

# Delete the resource group when done with the application
az group delete --name rg-quickstart-aks-payg-001 --yes --no-wait
```

Helps:

- [az aks](https://docs.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest)
- [Service principals with Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/kubernetes-service-principal)
- [Recommended naming and tagging conventions](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/naming-and-tagging)
- [Understand Kubernetes cluster performance with Azure Monitor for containers](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/container-insights-analyze)
