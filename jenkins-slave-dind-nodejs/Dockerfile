FROM registry.aliyuncs.com/acs-sample/jenkins-slave-dind:0.1

ENV PATH /root/bin:$PATH

ADD ./node ./node

ENV NPM_CONFIG_LOGLEVEL info
ENV NODE_VERSION 8.9.0

RUN tar -xJf "./node/node-v$NODE_VERSION-linux-x64.tar.xz" -C /usr/local --strip-components=1 \
  && rm -rf ./node

RUN set -x \
    && apt-get -qq update \
    && apt-get install -qqy apt-utils \
    && apt-get -qq upgrade \
    && apt-get -qq dist-upgrade \
    && apt-get install -qqy \
        npm \
        sudo \
        wget

CMD ["/usr/sbin/sshd", "-D"]
