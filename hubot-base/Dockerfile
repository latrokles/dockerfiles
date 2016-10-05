FROM latrokles/base-env:latest
MAINTAINER latrokles@gmail.com

RUN apt-get update && apt-get upgrade -y  && apt-get install -y \
    build-essential

RUN curl --silent --location https://deb.nodesource.com/setup_0.12 | bash -
RUN apt-get install --yes nodejs
