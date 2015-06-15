FROM williamyeh/java8:latest
MAINTAINER Megam systems <info@megam.io>

# install wget
RUN apt-get install -y wget

RUN apt-get -y install curl

ENV SBT_VERSION 0.13.7
ENV SBT_HOME /usr/local/sbt
ENV PATH ${PATH}:${SBT_HOME}/bin

# Install sbt
RUN curl -sL "http://dl.bintray.com/sbt/native-packages/sbt/$SBT_VERSION/sbt-$SBT_VERSION.tgz" | gunzip | tar -x -C /usr/local && \
    echo -ne "- with sbt $SBT_VERSION\n" >> /root/.built

#Install git
RUN apt-get -y install git

#clone megam nilavu
RUN git clone https://github.com/megamsys/megam_gateway.git -b 0.8

# Install Rails App
WORKDIR /megam_gateway

EXPOSE 9000

# fetches all sbt jars from Maven repo so that your sbt will be ready to be used when you launch the image
CMD ["sbt clean compile run"]
