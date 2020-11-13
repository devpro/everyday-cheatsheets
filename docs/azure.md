# Azure CLI (Command-Line Interface) Cheat Sheet

[Documentation](https://docs.microsoft.com/en-us/cli/azure/?view=azure-cli-latest)

## Installation

You can [Install the Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) on any platform, Windows or Linux (including Windows Subsystem for Linux)

## Basic commands

Command | Action
------- | ------
`az --version` | Check the CLI version
`az --help` | Display help information
`az login` | Login to a specific Azure user account (will open a web page in a browser)
`az account list` | List all subscriptions you have access
`az account set --subscription "xxxxx-xxxx-xxxx-xxxx-xxxxxx"` | Set the current context to a specific subscription
`az account show` | Display the current context

## Recipes

-  [Configure registry credentials in web app](https://docs.microsoft.com/en-us/azure/app-service/containers/tutorial-custom-docker-image#configure-registry-credentials-in-web-app)

`az webapp config container set --name mywebappresourcename --resource-group myresourcegroup --docker-custom-image-name mycontainerregistry.azurecr.io/repositorytname:imagetag --docker-registry-server-url https://mycontainerregistry.azurecr.io --docker-registry-server-user myacruser --docker-registry-server-password myacrpassword`

- [Create an App Service app and deploy files with FTP using Azure CLI](https://docs.microsoft.com/en-us/azure/app-service/scripts/cli-deploy-ftp)
