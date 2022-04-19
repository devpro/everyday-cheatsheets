# K3s

> K3s is a CNCF sandbox project that delivers a lightweight yet powerful certified Kubernetes distribution. When used with SUSE Rancher, K3s is ideal for running production workloads across resource-restrained, remote locations or on IoT devices.

→ [k3s.io](https://k3s.io/), [docs](https://rancher.com/docs/k3s/latest/en/), [GitHub](https://github.com/k3s-io/k3s),
[suse.com/products/k3s](https://www.suse.com/products/k3s/)

## General idea 

<img src="https://k3s.io/img/how-it-works-k3s-revised.svg" style="width:1000px">

## Quick start

### Install

### Run in a container with k3d

> k3d is a lightweight wrapper to run k3s (Rancher Lab’s minimal Kubernetes distribution) in docker.

→ [k3d.io](https://k3d.io/) ([GitHub](https://github.com/k3d-io/k3d))

#### Create a cluster with k3d

```bash
# runs installation script
wget -q -O - https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash

# creates a cluster
k3d cluster create firstcluster

# displays nodes
kubectl get nodes

# deletes a cluster
k3d cluster delete firstcluster
```

### Run in a Linux system

* [Quick-Start Guide](https://rancher.com/docs/k3s/latest/en/quick-start/)
