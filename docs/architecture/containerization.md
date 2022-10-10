# Containerization

## Big picture

![Container evolution](https://d33wubrfki0l68.cloudfront.net/26a177ede4d7b032362289c6fccd448fc4a91174/eb693/images/docs/container_evolution.svg)

Source: [Kubernetes Documentation Concepts Overview](https://kubernetes.io/docs/concepts/overview/)

## Definitions

### What is a container?

> A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.

→ [Docker](https://www.docker.com/resources/what-container/)

See also [Microsoft](https://azure.microsoft.com/en-us/resources/cloud-computing-dictionary/what-is-a-container/)

### What is Containerization?

> Containerization is the packaging together of software code with all it’s necessary components like libraries, frameworks, and other dependencies so that they are isolated in their own “container”.

→ [Red Hat](https://www.redhat.com/en/topics/cloud-native-apps/what-is-containerization)

## Components

### Container runtimes

* [Docker](../docker/docker.md)
* [containerd](../cncf/containerd.md)
* [cri-o](../cncf/cri-o.md)
* [podman](../podman.md)

See also [aqua](https://www.aquasec.com/cloud-native-academy/container-platforms/container-engines/)

### Container registries

* [Docker Hub](https://hub.docker.com/)
* [Google Container Registry](https://cloud.google.com/container-registry/)
* [Red Hat Quay](https://www.redhat.com/en/technologies/cloud-computing/quay)

### Container GUI

* [Docker Desktop](https://www.docker.com/products/docker-desktop)
* Rancher Desktop

## Readings

* [Containers vs. Pods - Taking a Deeper Look](https://iximiuz.com/en/posts/containers-vs-pods/) - October 28, 2021
