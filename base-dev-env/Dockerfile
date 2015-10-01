FROM latrokles/base-env:latest
MAINTAINER latrokles@gmail.com

RUN apt-get update && apt-get install -y \
    build-essential

ENV user latrokles
ENV HOME /home/${user}
RUN useradd --create-home --home-dir $HOME ${user} \
        && mkdir -p $HOME/workspace \
        && chown -R ${user}:${user} $HOME

RUN chsh ${user} -s /usr/bin/zsh
WORKDIR $HOME
USER ${user}
CMD ["zsh"]
