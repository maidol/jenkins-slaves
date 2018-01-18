FROM registry.aliyuncs.com/acs-sample/jenkins-slave-dind:0.1

MAINTAINER Ringtail <zhongwei.lzw@alibaba-inc.com>

# gcc for cgo
RUN apt-get update && apt-get install -y --no-install-recommends \
		g++ \
		gcc \
		libc6-dev \
		make \
	&& rm -rf /var/lib/apt/lists/*

ENV GOLANG_VERSION 1.9.2

RUN tar -C /usr/local -xzf "./go/go$GOLANG_VERSION.linux-amd64.tar.gz" \
  && rm -rf ./go

ENV GOPATH /go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"
WORKDIR $GOPATH

COPY go-wrapper /usr/local/bin/

CMD ["/usr/sbin/sshd", "-D"]
