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
I personally run this by mapping the container's user home to my own host's
user home directory as I have dotfiles and vim (vimrc + plugins) set up there,
but this is not a requirement as you can simply checkout your own dotfiles and
source repositories directly into the container for temporary work.

```
docker run -it \
        -v ${HOME}:/home/${user} \
        --name dev-base \
        latrokles/base-dev-env:latest
```
