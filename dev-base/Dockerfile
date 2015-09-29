# TO BUILD use:
#   docker build -t latrokles/dev-base:1.0 .

# TO RUN use: 
#   docker run -it \
#          -v ~/workspace:/home/${user}/workspace \
#          -v ~/vim:/home/${user}/.vim \
#          --name dev-base \
#          latrokles/dev-base:1.0

FROM debian:jessie
RUN awk '$1 ~ "^deb" { $3 = $3 "-backports"; print; exit  }' /etc/apt/sources.list > /etc/apt/sources.list.d/backports.list

RUN apt-get update && apt-get install -y \
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
RUN su -m ${user} && cd
RUN git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
ENV DOTFILES ${HOME}/workspace/config/dotfiles
RUN echo "source ${DOTFILES}/.zshrc" > $HOME/.zshrc
RUN echo "source ${DOTFILES}/.alias" > $HOME/.zshrc
RUN ln -s ${DOTFILES}/.vimrc ~/.vimrc

WORKDIR $HOME
USER ${user}
CMD ["zsh"]
