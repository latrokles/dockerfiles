FROM mhart/alpine-node:4
MAINTAINER latrokles@gmail.com

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
ENV PATH ${NPM_MODULE_DIR}:${NPM_MODULE_DIR}/bin:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin

WORKDIR ${HOME}
ENTRYPOINT ["sh"]
