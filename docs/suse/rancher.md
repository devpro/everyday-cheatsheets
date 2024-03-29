# Rancher

> Rancher is a container management platform built for organizations that deploy containers in production. Rancher makes it easy to run Kubernetes everywhere, meet IT requirements, and empower DevOps teams.

→ [rancher.com](https://rancher.com/), [docs](https://rancher.com/docs/rancher/v2.6/en/)

## General idea

![Rancher platform](https://rancher.com/docs/img/rancher/platform.png)

## Quick start

* [Get Started with SUSE Rancher in 2 Easy Steps](https://www.suse.com/products/suse-rancher/get-started/)
(see also [Installing Rancher on a Single Node Using Docker](https://rancher.com/docs/rancher/v2.6/en/installation/other-installation-methods/single-node-docker/))

```bash
# creates Rancher container
sudo docker run --privileged -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher

# manual: open http://localhost and follow instructions to login, at the end download the kubeconfig file

# sets kubectl to the Kubernetes cluster and displays the single node
export KUBECONFIG=local.yaml
kubectl get nodes
```
