# GitLab

→ [gitlab.com](https://about.gitlab.com/)

## Hosting solutions

- [gitlab.com (SaaS)](https://gitlab.com/)
- On-Premises
  - [Docker](https://docs.gitlab.com/ee/install/docker.html): [gitlab/gitlab-ee](https://hub.docker.com/r/gitlab/gitlab-ee/), [gitlab/gitlab-ce](https://hub.docker.com/r/gitlab/gitlab-ce/)

## Runners

- Local execution

  - Use Docker image (workaround found on [gitlab-runner issue#4275](https://gitlab.com/gitlab-org/gitlab-runner/-/issues/4275))

  ```bash
  # creates local folder
  mkdir -p .gitlab/runner/local
  
  # displays help on a command
  docker run --rm --name gitlab-runner -v /var/run/docker.sock:/var/run/docker.sock -v $PWD/.gitlab/runner/local/config:/etc/gitlab-runner -v $PWD:$PWD --workdir $PWD gitlab/gitlab-runner exec help
  
  # executes shell on "build" job
  docker run --rm --name gitlab-runner -v /var/run/docker.sock:/var/run/docker.sock -v $PWD/.gitlab/runner/local/config:/etc/gitlab-runner -v $PWD:$PWD --workdir $PWD gitlab/gitlab-runner exec shell build
  
  # executes docker on "build" job (use image defined in the gitlab-ci file)
  docker run --rm --name gitlab-runner -v /var/run/docker.sock:/var/run/docker.sock -v $PWD/.gitlab/runner/local/config:/etc/gitlab-runner -v $PWD:$PWD --workdir $PWD gitlab/gitlab-runner exec shell build
  ```

  - Includes are not supported unfortunately
    - Issue(s): [Local runner execution MVC](https://gitlab.com/gitlab-org/gitlab-runner/-/issues/2797)
    - Alternative(s): [firecow/gitlab-ci-local](https://github.com/firecow/gitlab-ci-local)
