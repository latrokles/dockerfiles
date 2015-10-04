FROM latrokles/base-dev-env:latest
MAINTAINER latrokles@gmail.com

# install RVM
USER root
RUN apt-get update && apt-get upgrade -y && apt-get install -y \
    autoconf \
    automake \
    bison \
    gawk \
    libffi-dev \
    libgdbm-dev \
    libncurses5-dev \
    libreadline6-dev \
    libsqlite3-dev \
    libssl-dev \
    libtool \
    libyaml-dev \
    pkg-config \
    sqlite3 \
    zlib1g-dev 

USER ${user}
RUN cd
RUN gpg --keyserver hkp://keys.gnupg.net \ 
    --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
RUN curl -sSL https://get.rvm.io | bash -s stable --ruby

# set up RVM for use
USER ${user}
RUN cd
RUN echo "source /home/latrokles/.rvm/scripts/rvm" >> ${HOME}/.zshrc
RUN echo \
    "[[ -r $rvm_path/scripts/completion  ]] && . $rvm_path/scripts/completion" \ 
    >> ${HOME}/.zshrc
