# Cloud Foundry

> Cloud Foundry is an Open Source Cloud Application Platform.

→ [cloudfoundry.org](https://www.cloudfoundry.org/), [GitHub](https://github.com/cloudfoundry), [Incubator](https://github.com/cloudfoundry-incubator)

## Learn

- [Read the docs](https://docs.cloudfoundry.org/#read-the-docs)
- [Developer Guide](https://docs.cloudfoundry.org/devguide/)

### Key features

- [Overview](https://docs.cloudfoundry.org/concepts/overview.html)

<IMG src="https://docs.cloudfoundry.org/concepts/images/power-of-platform.png" alt="The Power of the Platform"/>

- [Security](https://docs.cloudfoundry.org/concepts/security.html)

  - Typical deployment

<IMG src="https://docs.cloudfoundry.org/concepts/images/security/sysbound1.png" alt="Sysbound1"/>

- [Routing](https://docs.cloudfoundry.org/concepts/cf-routing-architecture.html)

- [HTTP Routing](https://docs.cloudfoundry.org/concepts/http-routing.html)

<IMG src="https://docs.cloudfoundry.org/concepts/images/cf-routing-architecture.png" alt="Diagram of Cloud Foundry routing architecture"/>

- [Container management](https://docs.cloudfoundry.org/concepts/diego/diego-architecture.html)
  - Diego Cell components
  - Diego Brain components

<IMG src="https://docs.cloudfoundry.org/concepts/images/diego/diego-flow.png" alt="Diego flow"/>

- [Container networking](https://docs.cloudfoundry.org/concepts/understand-cf-networking.html)

<IMG src="https://docs.cloudfoundry.org/concepts/images/c2c-arch.png" alt="c2c architecture diagram"/>

- [Service discovery](https://github.com/cloudfoundry/cf-networking-release/blob/develop/docs/app-sd.md)

  - In order to support all types of apps, languages and frameworks, we built service discovery for c2c into the platform. With this feature, users no longer have to bring their own service discovery.
  - [Cats and Dogs](https://github.com/cloudfoundry/cf-networking-examples/blob/master/docs/c2c-with-service-discovery.md)

- [Cloud Controller](https://docs.cloudfoundry.org/concepts/architecture/cloud-controller.html)

<IMG src="https://docs.cloudfoundry.org/concepts/images/cc-communications-map.png" alt="Cc communications map"/>

### Glossary

- [Buildpacks](https://docs.cloudfoundry.org/buildpacks/) provide framework and runtime support for apps. Buildpacks typically examine your apps to determine what dependencies to download and how to configure the apps to communicate with bound services.

- [**BOSH**](https://bosh.io/docs/) is an open source tool chain for release engineering, deployment and lifecycle management of large scale distributed services ([GitHub](https://github.com/cloudfoundry/bosh)).

- [CFAR](https://www.cloudfoundry.org/application-runtime/), Cloud Foundray Application Runtime, is a code-centric platform that simplifies the life of developers (previously known as Elastic Runtime). It takes your code, written in any language or framework, and runs it on any cloud. This flexibility extends to services as well, thanks to the Open Service Broker API, which makes it easy to integrate the services your apps need to run.

- [CFCR](https://www.cloudfoundry.org/container-runtime/), Cloud Foundray Container Runtime, is an open-source project that provides a solution for deploying and managing Kubernetes clusters using BOSH. See [Welcome to CFCR](https://docs-cfcr.cfapps.io/).

- [CAPI](https://docs.cloudfoundry.org/devguide/capi/client-libraries.html) stands for Cloud Controller API.

- [CredHub](https://docs.cloudfoundry.org/credhub/index.html) is a component designed for centralized credential management in Cloud Foundry (CF). It is a single component that can address several scenarios in the CF ecosystem. At the highest level, CredHub centralizes and secures credential generation, storage, lifecycle management, and access.

- [**Diego**](https://docs.cloudfoundry.org/concepts/diego/diego-architecture.html) is the container management system for Cloud Foundry ([cloudfoundry/diego-release](https://github.com/cloudfoundry/diego-release)).

- [**Garden**](https://docs.cloudfoundry.org/concepts/architecture/garden.html) is the component that Cloud Foundry uses to create and manage isolated environments called containers. Each instance of an application deployed to Cloud Foundry runs within a container.

- [Gorouter](https://docs.cloudfoundry.org/concepts/architecture/router.html) routes traffic coming into Cloud Foundry to the appropriate component, whether the request comes from an operator addressing the Cloud Controller or from an application user accessing an app running on a Diego Cell. Handling both platform and app requests with the same process centralizes routing logic and simplifies support for WebSockets and other types of traffic (for example, through HTTP CONNECT). See [GitHub](https://github.com/cloudfoundry/gorouter).

- [GrootFS](https://github.com/cloudfoundry/grootfs) is the container root filesystem management component for Garden. A container root filesystem or rootfs is often referred to as an _image_. See [Blog entry](https://www.cloudfoundry.org/blog/grootfs-container-image-management-cloud-foundry/).

- [NATS](https://docs.cloudfoundry.org/concepts/architecture/messaging-nats.html) is a lightweight publish-subscribe and distributed queueing messaging system written in Ruby ([GitHub](https://github.com/nats-io/ruby-nats)).

- [Stemcell](https://bosh.io/docs/stemcell/) is a versioned Operating System image wrapped with IaaS specific packaging.
  - [cloudfoundry-incubator/stembuild](https://github.com/cloudfoundry-incubator/stembuild): The stembuild binary is used to build BOSH stemcells for Windows 2012R2,Windows Server, version v1709, Windows Server, version 1803, Windows Server 2019 on vSphere.
  - [cloudfoundry-community/stembuild-concourse](https://github.com/cloudfoundry-community/stembuild-concourse): A concourse pipeline to create a Windows stemcell using stembuild cli.
  - [Creating a Windows Stemcell for vSphere Using stembuild (Beta)](https://docs.pivotal.io/pivotalcf/2-6/windows/create-vsphere-stemcell-automatically.html)
  - [Downloading or Creating Windows Stemcells](https://docs.pivotal.io/pivotalcf/2-5/windows/stemcells.html)
  - [Stemcells for PCF (Windows)](https://network.pivotal.io/products/stemcells-windows-server)

- [UAA](https://docs.cloudfoundry.org/concepts/architecture/uaa.html) stands for User Account and Authentication.

### Going further

- [Slack](https://cloudfoundry.slack.com)

## Command line

```bash
cf version

cf --version

cf --version

cf --version

cf --help

cf <command> -h

cf login -a <cf-api-endpoint>

cf target

cf push pal-tracker --random-route -p src/PalTracker/bin/Release/netcoreapp2.1/publish

cf set-env pal-tracker WELCOME_MESSAGE "Hello from Cloud Foundry"

cf restart pal-tracker

cf delete pal-tracker

cf map-route

cf marketplace

cf create-service cleardb spark tracker-database

cf bind-service pal-tracker tracker-database
```

## Recipes

### Integrate with Kubernetes

* [CF for k8s](https://cf-for-k8s.io/)
  * [The New Stack > Using Grafana to Monitor Cloud Foundry Objects and Apps Running on Kubernetes](https://thenewstack.io/using-grafana-to-monitor-cloud-foundry-objects-and-apps-running-on-kubernetes/) - March 5, 2021
