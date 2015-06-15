FROM ubuntu:14.04
MAINTAINER Megam systems <info@megam.io>

# reduce output from debconf
ENV DEBIAN_FRONTEND noninteractive

# Intall software-properties-common for add-apt-repository
RUN apt-get install -qq -y software-properties-common

RUN add-apt-repository ppa:openjdk-r/ppa

RUN apt-get update

RUN apt-get install -y openjdk-8-jdk

RUN update-alternatives --config java

RUN update-alternatives --config javac

# define default command
CMD ["java"]

