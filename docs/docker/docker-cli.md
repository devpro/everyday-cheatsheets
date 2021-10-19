# Docker CLI

## Examples

```bash
# builds a new image
docker build . -t myrepo/myimage:mytag -f mypath\Dockerfile --no-cache

# runs a new container
docker run -p 8011:80 -e ASPNETCORE_ENVIRONMENT=Development --name mycontainername myrepo/myimage:mytag
```
