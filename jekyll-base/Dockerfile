FROM latrokles/base-env:latest
MAINTAINER latrokles@gmail.com

RUN apt-get update && apt-get upgrade -y && apt-get install -y \
    build-essential \
    ruby-dev \
    rubygems \
    python2.7

RUN gem install rubygems-update --no-doc --no-ri
RUN gem install jekyll therubyracer json --no-doc --no-ri

ENV user jekyll
ENV HOME /home/${user}
RUN useradd --create-home --home-dir $HOME ${user}
RUN chown -R ${user}:${user} ${HOME}

USER ${user}
WORKDIR ${HOME}
