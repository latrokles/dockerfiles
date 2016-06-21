FROM alpine:3.3
MAINTAINER latrokles@gmail.com

# packages to install
ENV BUILD_PACKAGES bash tree curl-dev ruby-dev build-base libxml2-dev
ENV DEV_PACKAGES zlib-dev libxml2-dev libxslt-dev tzdata yaml-dev sqlite-dev postgresql-dev mysql-dev
ENV RUBY_PACKAGES ruby ruby-io-console
ENV APP_PACKAGES sqlite

RUN apk update
RUN apk upgrade
RUN apk add ${BUILD_PACKAGES} ${DEV_PACKAGES} ${RUBY_PACKAGES} ${APP_PACKAGES}

# create user
ENV user developer
RUN /usr/sbin/adduser -D ${user}

# set up user's path and gem home 
USER ${user}
ENV workspace /home/${user}/workspace
RUN mkdir ${workspace}
RUN echo export PATH="$(ruby -rubygems -e 'puts Gem.user_dir')/bin:$PATH" >> ~/.bashrc
RUN echo export GEM_HOME="$(ruby -rubygems -e 'puts Gem.user_dir')" >> ~/.bashrc
RUN echo "gem: --no-rdoc --no-ri" >> ~/.gemrc

# setup bundler
RUN gem install -N bundler --user-install

# setup for startup
WORKDIR ${workspace}
CMD ["bash"]
