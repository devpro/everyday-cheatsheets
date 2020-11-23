# Docker Cheat Sheet

[docker.com](https://www.docker.com/) > [docs](https://docs.docker.com/)

## Docker Desktop

[Docker Desktop](https://www.docker.com/products/docker-desktop)

### Installation on Windows

[Install Docker for Windows](https://docs.docker.com/docker-for-windows/install/#start-docker-for-windows)

See [WSL cheat sheet](https://github.com/devpro/everyday-cheatsheets/blob/master/docs/wsl.md).

### Installation on WSL 1 (Ubuntu)

[Installing the Docker client on Windows Subsystem for Linux (Ubuntu)](https://medium.com/@sebagomez/installing-the-docker-client-on-ubuntus-windows-subsystem-for-linux-612b392a44c4)

Once docker is installed on Ubuntu, configure Docker on Windows to expose port 2375 and run:

```bash
$ docker images
#Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
$ docker -H localhost:2375 images
#Cannot connect to the Docker daemon at tcp://localhost:2375. Is the docker daemon running?
$ docker -H localhost:2375 images
#REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
#ubuntu              latest              f975c5035748        4 weeks ago         112MB
```

### Installation on Ubuntu

[Get Docker CE for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/#set-up-the-repository)

## Docker CLI

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

## Quickstart

[Get Started](https://docs.docker.com/get-started/)

### Playground

- [Play with Docker (PWD)](https://labs.play-with-docker.com/)

### Tutorials

- [Docker 101 Tutorial](https://www.docker.com/101-tutorial)

- Hello world (will display "Hello from Docker!")

```bash
docker run hello-world
```

- Ubuntu bash

```dos
docker run -it ubuntu bash
apt-get update
apt-get upgrade
apt-get install apt-utils
apt-get install traceroute
traceroute www.google.fr
apt-get install wget
wget --spider http://example.com
```
