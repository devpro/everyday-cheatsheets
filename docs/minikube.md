# Minikube

> Local Kubernetes, focused on application development & education

[minikube.sigs.k8s.io](https://minikube.sigs.k8s.io/) [GitHub](https://github.com/kubernetes/minikube)

## Quick start

### Installation

Follow the instructions given in the [Getting Started page](https://minikube.sigs.k8s.io/docs/start/).

More information on [Installing Kubernetes with Minikube page](https://kubernetes.io/docs/setup/learning-environment/minikube/).

If you're on Windows, remember to open a command window as admin.

### Run/stop

If you're on Windows, make [Hyper-V driver](https://minikube.sigs.k8s.io/docs/reference/drivers/hyperv/) the default driver: `minikube config set vm-driver hyperv`.

Run `minikube start` to start the Kubernetes node and `minikube stop` to stop it.

### Clean-up

Run `minikube delete` and, if needed, delete the `.kube` and `.minikube` folder in your home directory.

### Dashboard

Run `minikube dashboard` to open the web dashboard.

### Kubernetes CLI

Run `kubectl config use-context minikube` to be able to use kubectl on your local Kubernetes instance.

## CLI reference

Command | Action
------- | ------
`minikube service xxx --url` | Display url for a given service (xxx)
`minikube config set memory 4096` | Set memory value (2048 by default)
