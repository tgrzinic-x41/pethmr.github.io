# Pet-HMR website

This repository contains the Pet-HMR webpage.

## Development and usage

Use a container to host Ruby modules that are needed to run the Jekyll build process.
You must build the container on your machine. Thus user inside the container will have
your users uid and gid and thus not add "foreign" files to your home dir, when mount the 
project folder into the container.

```
# Currently the scripts only support linux

# Build
./build_docker.sh

# Run
./start_docker.sh

# Building for prod
./generate.sh

# Running locally for testing (will automatically do a prod build and 
# host with pyhton's internal web server)
./serve.sh

# Publishing to github:
# 1) Commit all your changes to the master branch (do not commit / push the _site folder)
#       Or create a PR
# 2) Checkout gh-pages-local
# 3) pull remote changes
# 4) merge the (local) master 
# 5) build the site
# 6) commit and push (including the _site folder) 
# 7) Push the _site folder to the gh-pages branch with

git subtree push --prefix _site origin gh-pages

```

In the container for rebuilding run:
```
bundle exec jekyll clean && bundle exec jekyll build
```

Use the Python internal web server to host the page for testing purposes

```
cd _site; python3 -m http.server
```

## Deployment
