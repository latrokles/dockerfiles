FROM latrokles/base-env:latest
MAINTAINER latrokles@gmail.com

RUN apt-get update && apt-get upgrade -y  && apt-get install -y \
    build-essential

RUN curl --silent --location https://deb.nodesource.com/setup_6.x | bash -
RUN apt-get install --yes nodejs
