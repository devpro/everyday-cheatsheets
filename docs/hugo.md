# Hugo

> Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again.

→ [gohugo.io](https://gohugo.io/)

## Getting started

- [Installation](https://gohugo.io/installation/)

### Local run

To have the website running locally, with automatic reload, follow the steps:

- Get the source code through `git clone --recurse-submodules`
- Run locally with `hugo server -D`

### Add content

- Create a new page with the command `hugo new path/to/new/file.md`
- Look at [fontawesome.com](https://fontawesome.com/icons?d=gallery) for ideas of menu icons

### Known issues

- If Git is saying one theme submodule is in dirty state run `git submodule foreach --recursive git checkout .` (see [the discussion on stackoverflow](https://stackoverflow.com/questions/4873980/git-diff-says-subproject-is-dirty))
- Folders starting with a dot (".") will not be served by nginx (available from static folders for instance)

### Examples

- `.gitmodules` file

```ini
[submodule "themes/hugo-theme-learn"]
  path = themes/hugo-theme-learn
  url = https://github.com/matcornic/hugo-theme-learn.git
```

- `config.toml` file

```toml
baseURL = "https://knowledge-base-bertrand-thomas.cfapps.io/"
languageCode = "en-us"
title = "Bertrand Thomas Knowledge Base"
theme = "hugo-theme-learn"

[params]
# Change default color scheme with a variant one. Can be "red", "blue", "green".
themeVariant = "blue"

[outputs]
home = [ "HTML", "RSS", "JSON" ]
```

## Automate

- Example of Circle CI pipeline

```yaml
version: 2
jobs:
  build:
    docker:
      # See https://hub.docker.com/r/cibuilds/hugo, https://github.com/cibuilds/hugo
      - image: cibuilds/hugo:0.58.3

    steps:
      - checkout
      - run:
          name: Install git client
          command: apk update && apk add git
      - run:
          name: Load submodule
          command: git submodule sync && git submodule update --init
      - run:
          name: Build Hugo static website
          command: HUGO_ENV=production hugo
      - run:
          name: Install CF CLI
          command: |
            apk add wget
            wget https://cli.run.pivotal.io/stable?release=linux64-binary
            mv stable?release=linux64-binary /tmp/cf-cli.tgz
            mkdir -p /usr/local/bin
            tar -xzf /tmp/cf-cli.tgz -C /usr/local/bin
            cf --version
            rm -f /tmp/cf-cli.tgz
      - run:
          name: Deploy
          command: |
            cf login -a "$CF_API" -u "$CF_USERNAME" -p "$CF_PASSWORD" -o "$CF_ORG" -s "$CF_SPACE_PROD"
            cf push
```

## Deploy

### Deployment procedure

- Create the static content by running `HUGO_ENV=production hugo` (only not draft posts will be published!)
