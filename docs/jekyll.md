# Jekyll

→ [Jekyll](https://jekyllrb.com/)

## How to run locally

### Requirements

- Install [Ruby]
  - On Windows, download the latest version with DevKit from the [Download page](https://rubyinstaller.org/downloads/) and execute it, agree to run `ridk install` at the end

- Install jekyll gem
  - Run `gem install bundler jekyll`

### Local server

Open the terminal at the root folder and run `bundle exec jekyll serve`

## How to contribute

## Creation

This code base was made by using the command: `jekyll new my-website`

## How to run with Docker

```bash
# checks docker is working
docker run hello-world

# checks make utility is present
make --version

# creates a new projet
mkdir jekyll-site
cd jekyll-site
docker run -v $(pwd):/srv/jekyll jekyll/jekyll:latest jekyll new .

# starts web server (open http://localhost:4000/ in a browser)
docker run -v $(pwd):/srv/jekyll -p 4000:4000 -it jekyll/jekyll:latest jekyll serve
```

See [alcher.dev](https://alcher.dev/2020/jekyll-on-docker/)
