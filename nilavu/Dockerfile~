FROM ubuntu:14.04
MAINTAINER Megam systems <info@megam.io>

# reduce output from debconf
ENV DEBIAN_FRONTEND noninteractive
ENV PATH /usr/local/rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV RUBY_VERSION ruby-2.2.2

# Intall software-properties-common for add-apt-repository
RUN apt-get install -qq -y software-properties-common

RUN apt-get -y install curl

# Install RVM
RUN gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
RUN curl -L https://get.rvm.io | bash -s stable

# Install Ruby
RUN echo 'source /usr/local/rvm/scripts/rvm' >> /etc/bash.bashrc
RUN /bin/bash -l -c 'rvm requirements'
RUN /bin/bash -l -c 'rvm install $RUBY_VERSION'
RUN /bin/bash -l -c 'rvm alias create default $RUBY_VERSION'
RUN /bin/bash -l -c 'rvm rubygems current'

# Install bundler
RUN /bin/bash -l -c 'gem install rubygems-bundler --no-doc --no-ri'

#Install git
RUN apt-get -y install git

#clone megam nilavu
RUN git clone https://github.com/megamsys/nilavu.git -b 0.8

# Install Rails App
WORKDIR /nilavu

RUN /bin/bash -l -c 'bundle install'
RUN ls -la

ENV RAILS_ENV development

EXPOSE 3000

CMD /usr/local/rvm/gems/ruby-2.2.2/bin/bundle exec passenger start -p 3000 --max-pool-size 8
