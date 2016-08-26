FROM alpine:3.4

# packages to install
ENV BUILD_PACKAGES bash tree curl-dev ruby-dev ruby-irb build-base libxml2-dev
ENV DEV_PACKAGES nodejs zlib-dev libxml2-dev libxslt-dev tzdata yaml-dev sqlite-dev postgresql-dev mysql-dev
ENV RUBY_PACKAGES ruby ruby-io-console

RUN apk update
RUN apk upgrade
RUN apk add ${BUILD_PACKAGES} ${DEV_PACKAGES} ${RUBY_PACKAGES}
RUN rm -rf /var/cache/apk/*

# create user
ENV user developer
RUN /usr/sbin/adduser -D ${user}

# set up user's path and gem home (this can be moved to the general ruby dev)
USER ${user}
ENV workspace /home/${user}/workspace
RUN mkdir ${workspace}
RUN echo export PATH="$(ruby -rubygems -e 'puts Gem.user_dir')/bin:$PATH" >> ~/.bashrc
RUN echo export GEM_HOME="$(ruby -rubygems -e 'puts Gem.user_dir')" >> ~/.bashrc

# setup bundler and rails
RUN gem install -N bundler --user-install
RUN gem install -N nokogiri --user-install
RUN /bin/sh -c "export PATH=\"$(ruby -rubygems -e 'puts Gem.user_dir')/bin:$PATH\" && bundle config build.nokogiri \"--use-system-libraries\""
RUN /bin/sh -c "export PATH=\"$(ruby -rubygems -e 'puts Gem.user_dir')/bin:$PATH\" && bundle config build.nokogumbo \"--use-system-libraries\""
RUN gem install -N --user-install rails

WORKDIR ${workspace}
CMD ["bash"]
