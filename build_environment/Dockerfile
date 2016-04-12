FROM lambdalab/base
MAINTAINER lambdalab

RUN apt-get update

# install python
RUN apt-get install -y python-pip

# install ruby
RUN curl -sSL https://get.rvm.io | bash
RUN echo "source /etc/profile.d/rvm.sh; rvm install ruby-2.0.0-p481; gem install bundle" | bash

# install zip
RUN apt-get install -y zip

# ant, maven
RUN apt-get install -y ant maven

# install node js
RUN wget http://nodejs.org/dist/v0.12.2/node-v0.12.2-linux-x64.tar.gz --no-verbose
RUN tar -xf node-v0.12.2-linux-x64.tar.gz -C /opt
RUN rm node-v0.12.2-linux-x64.tar.gz
ENV PATH $PATH:/opt/node-v0.12.2-linux-x64/bin

# install proto compiler
RUN apt-get install -y libprotobuf-dev protobuf-compiler

# install thrift
RUN apt-get install -y libboost-dev libboost-test-dev libboost-program-options-dev libevent-dev automake libtool flex bison pkg-config g++ libssl-dev

# install mongo client, easy to test
RUN apt-get install -y mongodb-clients

# scm
RUN apt-get install -y git

# help jdk build
RUN apt-get install -y libcups2-dev libasound2-dev libfreetype6-dev libxtst-dev libxrender-dev

# install cmake
RUN apt-get install -y build-essential cmake texinfo libtool bc

# install intel omp so that it's header could be found by clang
RUN apt-get install -y libiomp-dev

# Hack to get around UID mismatch
RUN for i in $(seq 1000 1010); do useradd builder$i -m -u $i -G sudo,root; done

RUN echo "%sudo ALL=(ALL) NOPASSWD: /usr/bin/apt-get" >> /etc/sudoers

# Anddroid SDK mount point
ENV ANDROID_HOME /android-sdk-linux
RUN apt-get install -y lib32stdc++6 lib32z1
