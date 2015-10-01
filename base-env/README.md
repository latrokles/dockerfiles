# README

This is a base docker image from which I plan to build all the others. It
essentially builds a debian host with a few necessary tools should I ever
have the need to exec a shell into a container to do some additional 
troubleshooting. I don't expect these minor tools to use up a lot of space.

## To build:
```
docker build -t latrokles/base-env:latest .
```

## To run:
There is no real reason to launch a container from this bare image, but just
in case...

```
docker run -it \
        --name base-env \
        latrokles/base-env:latest \
```
