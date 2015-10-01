# README

Base image for a hubot setup. Plan to use this for development and testing.
I'd like to use it for deployment, but I plan to run my hubot instance on
a raspberry pi and this x86 images won't run on ARM. We'll see.

Would like to setup this along with a REDIS container to use as
Hubot's brain. This could be done with docker compose, but I'm 
not entirely familiar with compose... yet.

## To build:
```
docker build -t latrokles/hubot-base:latest .
```

## To run:
```
docker run -it \
        --name hubot-base \
        latrokles/hubot-base:latest
```
