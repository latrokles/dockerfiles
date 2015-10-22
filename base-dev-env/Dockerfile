FROM latrokles/base-env:latest
MAINTAINER latrokles@gmail.com

ENV OMZ_REPO git://github.com/robbyrussell/oh-my-zsh.git
ENV OMZ_DEST .oh-my-zsh
ENV DOTFILES_REPO https://github.com/latrokles/dotfiles.git
ENV DOTFILES ~/dotfiles

# Update installed packages and install base toolchain
RUN apt-get update && apt-get install -y \
    build-essential

# Create user and set up user
ENV user latrokles
ENV HOME /home/${user}
RUN useradd --create-home --home-dir $HOME ${user} \
        && mkdir -p $HOME/workspace \
        && chown -R ${user}:${user} $HOME
RUN chsh ${user} -s /usr/bin/zsh

# Do additional user setup for shells, vim, etc.
WORKDIR $HOME
USER ${user}

## Install oh-my-zsh
RUN git clone ${OMZ_REPO} ${OMZ_DEST}
## Setup user dotfiles
RUN git clone ${DOTFILES_REPO}
RUN echo "source ~/dotfiles/zshrc" >> $HOME/.zshrc

## Setup vim
RUN zsh ~/dotfiles/setup-vim.sh
CMD ["zsh"]
