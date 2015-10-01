FROM latrokles/base-env:latest
MAINTAINER latrokles@gmail.com

RUN apt-get update && apt-get upgrade -y  && apt-get install -y \
    build-essential

RUN curl --silent --location https://deb.nodesource.com/setup_0.12 | bash -
RUN apt-get install --yes nodejs

ENV user hubot
ENV HOME /home/${user}
RUN useradd --create-home --home-dir ${HOME} ${user} \
    && chown -R ${user} ${HOME}

RUN npm install -g yo generator-hubot
RUN npm install -g coffee-script
RUN npm install hubot -g
RUN npm install --save hubot-pubsub

RUN chown -R ${user}:${user} ${HOME}
USER ${user}
WORKDIR ${HOME}
