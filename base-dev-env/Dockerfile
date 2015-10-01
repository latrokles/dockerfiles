FROM debian:jessie
MAINTAINER latrokles@gmail.com

RUN awk '$1 ~ "^deb" { $3 = $3 "-backports"; print; exit  }' \
    /etc/apt/sources.list > /etc/apt/sources.list.d/backports.list

RUN apt-get update && apt-get install -y \
    build-essential \
    git \
    zsh \
    curl \
    tmux \
    vim

ENV user latrokles
ENV HOME /home/${user}
RUN useradd --create-home --home-dir $HOME ${user} \
        && mkdir -p $HOME/workspace \
        && chown -R ${user}:${user} $HOME

ENV LANG C.UTF-8

RUN chsh ${user} -s /usr/bin/zsh
WORKDIR $HOME
USER ${user}
CMD ["zsh"]
