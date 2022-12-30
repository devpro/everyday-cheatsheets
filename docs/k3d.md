# k3d

> k3d is a lightweight wrapper to run k3s (Rancher Lab’s minimal Kubernetes distribution) in docker.

→ [k3d.io](https://k3d.io/), [code](https://github.com/k3d-io/k3d)

## Installation

- Download & install latest release (ref. [k3d.io](https://k3d.io/v5.4.6/#install-current-latest-release))

```bash
# runs installation script
wget -q -O - https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

## Basic commands

Command                          | Action
-------------------------------- | ------
`k3d cluster create <mycluster>` | Create a cluster
`k3d cluster list`               | List the cluster
`k3d cluster delete <mycluster>` | Delete a cluster

## Getting started

- Create a cluster

```bash
# creates a cluster
k3d cluster create twonodecluster -p "8081:80@loadbalancer" -p "8082:443@loadbalancer" --agents 2

# kubectl configuration is automatically updated and set to use the new cluster context
kubectl get nodes

# traefik is deplayed as the default ingress controller (k3s behavior)
```

- Deploy a basic workflow (ref. [k3d Guides > Exposing Services](https://k3d.io/v5.1.0/usage/exposing_services/))

```bash
# creates a nginx (web server) deployment
kubectl create deployment nginx --image=nginx

# exposes the deployment with a service
kubectl create service clusterip nginx --tcp=80:80

# provides an ingress to the service
cat > nginx-ingress.yaml <<EOM
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: nginx
  annotations:
    ingress.kubernetes.io/ssl-redirect: "false"
spec:
  rules:
  - http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: nginx
            port:
              number: 80
EOM
kubectl apply -f nginx-ingress.yaml

kubectl get all -A -o wide
# makes sure 
curl localhost:8081/

# deletes a cluster
k3d cluster delete twonodecluster
```

## Advanced usage

- k3s deploys traefik as the default ingress controller

- Use load balancer (ref. [Kubernetes - K3D with Load Balancer](https://niehaitao.github.io/ops/ops-k3d-lb/))
