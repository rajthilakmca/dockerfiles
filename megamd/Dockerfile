FROM ubuntu:14.04
MAINTAINER Megam systems <info@megam.io>

ENV TERM linux
RUN apt-get -y update

# Download general prerequisites
RUN apt-get -y install wget bzip2 git-core bzr net-tools

# golang install
ENV VERSION 1.4.2
ENV OS linux
ENV ARCH amd64
RUN wget http://golang.org/dl/go$VERSION.$OS-$ARCH.tar.gz -q -O - | tar -zxf - -C /usr/local

# golang env
ENV GOPATH /go
ENV GOROOT /usr/local/go
ENV MEGAMD /megamd

ENV PATH $PATH:$GOROOT/bin:$MEGAMD

RUN mkdir go/
RUN mkdir go/src/
RUN mkdir go/src/github.com/
RUN mkdir go/src/github.com/megamsys

WORKDIR go/src/github.com/megamsys

#clone megam engine
RUN git clone https://github.com/megamsys/megamd.git

RUN pwd

# Install Rails App
WORKDIR megamd
RUN chmod 755 Makefile
RUN ./Makefile
RUN ls -la
RUN pwd

CMD ["make"]
