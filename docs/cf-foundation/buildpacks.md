# Buildpacks

> Buildpacks provide framework and runtime support for apps. Buildpacks typically examine your apps to determine what dependencies to download and how to configure the apps to communicate with bound services.
> When you push an app, Cloud Foundry automatically detects an appropriate buildpack for it. This buildpack is used to compile or prepare your app for launch.

[docs.cloudfoundry.org](https://docs.cloudfoundry.org/buildpacks/), [pivotal.io](https://pivotal.io/platform/pcf-components/buildpacks), [docs.pivotal.io](https://docs.pivotal.io/pivotalcf/2-6/buildpacks/)

## How do they work

- `bin/detect`: Can I handle this?
- `bin/supply`: If yes, provide the dependencies
- `bin/finalize`: Prepare the app for launch - runs only for the last buildpack
- `bin/release`: Build the metadata (env variables, start command, etc)

[Reference](https://basics-workshop.cloudfoundry.org/slides/#/38)

## Types

- Default buildpacks (included in the platform)
- [Community buildpacks](https://github.com/cloudfoundry-community/cf-docs-contrib/wiki/Buildpacks): Leverage the community
- Custom buildpacks: Build your own

## Examples

* [.NET Core buildpack](https://github.com/cloudfoundry/dotnet-core-buildpack)

## How to build

* [buildpack/pack](https://github.com/buildpack/pack)
* [Build and push an image from an app using a Cloud Native Buildpack](https://docs.microsoft.com/en-us/azure/container-registry/container-registry-tasks-pack-build)
