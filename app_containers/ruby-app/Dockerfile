FROM latrokles/base-env:latest
MAINTAINER latrokles@gmail.com

ENV APP_USER app_user
ENV APP_USER_HOME /home/app_user

# install RVM
USER root
RUN apt-get update && apt-get upgrade -y && apt-get install -y \
    autoconf \
    automake \
    bison \
    build-essential \
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

# set up app user
RUN useradd --create-home --home-dir ${APP_USER_HOME} ${APP_USER} && \
    chown -R ${APP_USER}.${APP_USER} ${APP_USER_HOME}
RUN chsh ${user} -s /usr/bin/zsh

# become app user
USER ${APP_USER}
RUN cd

# install rvm and deps
RUN gpg --keyserver hkp://keys.gnupg.net \ 
    --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
RUN curl -sSL https://get.rvm.io | bash -s stable --ruby
RUN echo "source ${APP_USER_HOME}/.rvm/scripts/rvm" >> ${APP_USER_HOME}/.zshrc
RUN ${APP_USER_HOME}/.rvm/scripts/rvm
RUN /usr/bin/zsh -l -c "gem install bundler"
