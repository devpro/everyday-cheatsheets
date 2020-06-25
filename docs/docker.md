# Docker Cheat Sheet

## Usual commands

Command | Action
------- | ------
`docker --version` | Display Docker CLI version
`docker info` | Display Docker general information
`docker container --help` | Display help for container command
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

See [Docker Cheat Sheet from Will Sargent](https://github.com/wsargent/docker-cheat-sheet).

Reference: [Child commands](https://docs.docker.com/engine/reference/commandline/docker/#child-commands)

## First steps

```dos
REM display hello world
docker run hello-world
```

```dos
REM run ubuntu
docker run -it ubuntu bash
apt-get update
apt-get install traceroute
traceroute www.google.fr
apt-get install wget
wget --spider http://example.com
```

Reference: [Get Started](https://docs.docker.com/get-started/)
