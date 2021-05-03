# Splunk

→ [splunk.com](https://www.splunk.com/)

## Getting started

### Local run with Docker

- Retrieve a specific [docker-Splunk](https://github.com/Splunk/docker-Splunk) image and run a new container

```bash
docker pull splunk/splunk:latest

# only from a linux based operating system (works with WSL)
docker run -d -p 8000:8000 -e SPLUNK_START_ARGS='--accept-license' -e SPLUNK_PASSWORD='<password>' splunk/splunk:latest
```

- Open [localhost:8000](http://localhost:8000) and login with admin and the password used in the command line
