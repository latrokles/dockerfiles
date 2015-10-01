FROM debian:jessie

RUN awk '$1 ~ "^deb" { $3 = $3 "-backports"; print; exit  }' \
    /etc/apt/sources.list > /etc/apt/sources.list.d/backports.list

RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    git \
    make

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

RUN chown -R ${user} ${HOME}
USER ${user}
WORKDIR ${HOME}
