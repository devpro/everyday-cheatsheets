# Azure CLI Cheat Sheet

`az login`

`az account list`

`az account set --subscription "xxxxx-xxxx-xxxx-xxxx-xxxxxx"`

`az webapp config container set --name mywebappresourcename --resource-group myresourcegroup --docker-custom-image-name mycontainerregistry.azurecr.io/repositorytname:imagetag --docker-registry-server-url https://mycontainerregistry.azurecr.io --docker-registry-server-user myacruser --docker-registry-server-password myacrpassword`
