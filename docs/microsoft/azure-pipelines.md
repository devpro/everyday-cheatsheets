# Azure Pipelines

→ [azure.microsoft.com/services/devops/pipelines](https://azure.microsoft.com/en-us/services/devops/pipelines/)

## Quick links

* [Documentation](https://docs.microsoft.com/en-us/azure/devops/pipelines/)

## Learn

### Latest features

* [Caching and faster artifacts in Azure Pipelines](https://devblogs.microsoft.com/devops/caching-and-faster-artifacts-in-azure-pipelines/) - July 24, 2019
* [New IP firewall rules for Azure DevOps Services](https://devblogs.microsoft.com/devops/new-ip-firewall-rules-for-azure-devops/) - May 31, 2019

### Agents

* [Microsoft-hosted agents](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/hosted?view=azure-devops&tabs=yaml) (public IP ranges)

### Definition

* [YAML schema reference](https://docs.microsoft.com/fr-fr/azure/devops/pipelines/yaml-schema)
* [Classic Editor VS. YAML](https://www.marcusfelling.com/blog/2020/azure-pipelines-classic-editor-vs-yaml/)

### Templates

[Template types & usage](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/templates)

### Variables

[Define variables](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/variables)

### Examples

Example of pipelines in [MicrosoftDocs](https://github.com/MicrosoftDocs) GitHub repositories.

.NET Blog article on [How the .NET Team uses Azure Pipelines to produce Docker Images](https://devblogs.microsoft.com/dotnet/how-the-net-team-uses-azure-pipelines-to-produce-docker-images/)

### Tutorials

* [Tutorial: Immutable infrastructure for Azure, using VSTS, Terraform, Packer and Ansible](https://cloudblogs.microsoft.com/opensource/2018/05/23/immutable-infrastructure-azure-vsts-terraform-packer-ansible/) May 23, 2018

## Recipes

### Code coverage

* [Generate Code Coverage Reports with ReportGenerator in Azure DevOps](https://ardalis.com/generate-code-coverage-reports-with-reportgenerator-in-azure-devops) - July 17, 2019
* [Uploading to Codecov just got easier](https://devblogs.microsoft.com/devops/uploading-to-codecov-just-got-easier/) - November 13, 2019

### Permissions

By default, it won't work for Artifacts, you need to click on "..." in the permission pane of your feed and click on "Allow project-scoped builds".

[Secure and share packages using feed permissions](https://docs.microsoft.com/en-us/azure/devops/artifacts/feeds/feed-permissions)

### Yaml

[Publish to NuGet feeds](https://docs.microsoft.com/en-us/azure/devops/pipelines/artifacts/nuget)

```yaml
- task: NuGetAuthenticate@0
  displayName: 'Authenticate to NuGet feed'
- task: NuGetCommand@2
  displayName: 'Push NuGet packages'
  inputs:
    command: 'push'
    packagesToPush: '$(Build.ArtifactStagingDirectory)/**/*.nupkg;!$(Build.ArtifactStagingDirectory)/**/*.symbols.nupkg'
    nuGetFeedType: 'internal'
    publishVstsFeed: $(azure.artifact.feed.id)
    allowPackageConflicts: true
```
