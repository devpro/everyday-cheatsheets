# Docker CLI

## Commands

→ [docs.docker.com](https://docs.docker.com/engine/reference/commandline/docker/)

### Main commands

Command | Action
------- | ------
`docker --version` | Display Docker CLI version
`docker info` | Display Docker general information
`docker container --help` | Displays help for container command
`docker container ls --all` | List all containers
`docker ps` | Get all running containers
`docker ps --all` | Get all containers
`docker rm <containerid>` | Delete a container by its id
`docker images` | Get all images on the system
`docker version` | Get Docker version (Client + Server)
`docker run hello-world` | Run Hello world image
`docker run -it ubuntu bash` | Run Ubuntu image with an interactive shell
`docker network ls` | List networks
`docker network inspect bridge` | Inspect network bridge
`docker exec -it <containerid> sh` | Execute a shell command on a running container
`docker start <containerid>` | Start an existing container
`docker stop <containerid>` | Stop a running container
`docker logs <containerid>` | See last logs of a container
`docker system prune --volumes` | Delete all unused objects ([pruning](https://docs.docker.com/config/pruning/))

### Examples

```bash
# builds a new image
docker build . -t myrepo/myimage:mytag -f mypath/Dockerfile --no-cache

# runs a new container
docker run -p 8011:80 -e ASPNETCORE_ENVIRONMENT=Development --name mycontainername myrepo/myimage:mytag
```

### Other cheat sheets

* [Will Sargent](https://github.com/wsargent/docker-cheat-sheet)
