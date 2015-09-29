# BUILD:
#   docker build -t latrokles/jekyll:latest .

# RUN:
#   docker run -d \
#          --name jekyll \
#          latrokles/jekyll:1.0
#

FROM debian:jessie
RUN apt-get update && apt-get upgrade -y && apt-get install -y \
    build-essential \
    ruby-dev \
    rubygems \
    python2.7

RUN gem install rubygems-update --no-doc --no-ri
RUN gem install jekyll therubyracer json --no-doc --no-ri
