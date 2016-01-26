FROM alpine:3.2
MAINTAINER latrokles@gmail.com

RUN apk add --update nodejs

ENV user dev
ENV HOME /home/${user}
RUN adduser -h $HOME -s sh -D ${user}

RUN mkdir -p $HOME/workspace && \
    chown -R ${user}:${user} $HOME

ENV NPM_MODULE_DIR /opt/npm
RUN mkdir -p ${NPM_MODULE_DIR}
RUN chown -R ${user}.${user} ${NPM_MODULE_DIR}

USER ${user}
RUN npm config set prefix ${NPM_MODULE_DIR}
ENV PATH ${NPM_MODULE_DIR}:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin
WORKDIR ${HOME}
CMD ["/bin/sh"]
