FROM alpine:3.3
MAINTAINER latrokles@gmail.com

ENV NODE_VERSION=v4.2.6 NPM_VERSION=2.14.12

RUN apk add --update git \
                     curl \
                     make \
                     gcc \
                     g++ \ 
                     python \
                     linux-headers \
                     libgcc \
                     libstdc++ \
                     binutils-gold && \ 
    curl -sSL https://nodejs.org/dist/${NODE_VERSION}/node-${NODE_VERSION}.tar.gz | \tar -xz && \
    cd /node-${NODE_VERSION} && \ 
    ./configure --prefix=/usr --without-snapshot --fully-static && \
    make -j$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) && \
    make install && \
    cd / && \
    npm install -g npm@${NPM_VERSION}

RUN apk del gcc \
            g++ \
            linux-headers \
            libgcc \
            libstdc++ \
            binutils-gold && \ 
    rm -rf /etc/ssl /node-${NODE_VERSION} /usr/include \ 
           /usr/share/man /tmp/* /var/cache/apk/* /root/.npm /root/.node-gyp \ 
           /usr/lib/node_modules/npm/man /usr/lib/node_modules/npm/doc \
           /usr/lib/node_modules/npm/html 

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
CMD ["/bin/sh"]
