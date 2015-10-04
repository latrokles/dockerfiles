# README

This builds a ruby development environment. It essentially installs rvm locally
for $user so that user can install additional dependencies locally and use them
for development and testing.

## To build:
```
docker build -t latrokles/ruby-dev-env:latest .
```

## To run:
```
docker run -it \
        -v ${HOME}/workspace/ruby:/home/${user}/workspace \
        --name ruby-dev \
        latrokles/ruby-dev-env:latest
```
