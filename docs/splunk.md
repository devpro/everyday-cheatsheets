# Splunk

> The Data-to-Everything Platform, Powering Security, IT and DevOps

→ [splunk.com](https://www.splunk.com/)

## Learn

- [meritis - Comment fonctionne Splunk ? [FR]](https://meritis.fr/comment-fonctionne-splunk/)

## Getting started

### Run locally with Docker

- Retrieve a specific [docker-Splunk](https://github.com/Splunk/docker-Splunk) image ([documentation](https://splunk.github.io/docker-splunk/)) and run a new container

```bash
docker pull splunk/splunk:latest

# only from a linux based operating system (works with WSL)
docker run -d -p 8000:8000 --name splunk -e SPLUNK_START_ARGS='--accept-license' -e SPLUNK_PASSWORD='<password>' splunk/splunk:latest
```

- Wait for the container to be ready (ok line in container logs)
- Open [localhost:8000](http://localhost:8000) and login with admin and the password used in the command line

Reference: [Deploy and run Splunk Enterprise inside a Docker container](https://docs.splunk.com/Documentation/Splunk/8.1.3/Installation/DeployandrunSplunkEnterpriseinsideDockercontainers)
