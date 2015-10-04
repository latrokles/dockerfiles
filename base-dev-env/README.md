# README

This repository builds a base development environment so as not to have to
install full toolchains on my own system. It also makes it portable so that
I need only install docker in another machine and run this container to get
a full development environment.

## To build:
```
docker build -t latrokles/base-dev-env:latest .
```

## To run:
```
docker run -it \
        -v ${HOME}/workspace:/home/${user}/workspace \
        --name dev-base \
        latrokles/base-dev-env:latest
```
