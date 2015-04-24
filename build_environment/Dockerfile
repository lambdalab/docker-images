FROM lambdalab/base
MAINTAINER zfy0701

RUN apt-get update

# install python
RUN apt-get install -y python-pip

# install ruby
RUN curl -sSL https://get.rvm.io | bash
RUN echo "source /etc/profile.d/rvm.sh; rvm install ruby-2.0.0-p481; gem install bundle" | bash

# ant, maven
RUN apt-get install -y ant maven

# sbt
RUN wget http://repo.scala-sbt.org/scalasbt/sbt-native-packages/org/scala-sbt/sbt/0.13.0/sbt.deb --no-verbose
RUN dpkg -i sbt.deb

# install gradle
RUN wget https://services.gradle.org/distributions/gradle-2.3-bin.zip --no-verbose
RUN unzip gradle-2.3-bin.zip -d /opt
RUN rm gradle-2.3-bin.zip
ENV PATH $PATH:/opt/gradle-2.3/bin

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
RUN apt-get install -y git mercurial subversion

# help jdk build
RUN apt-get install -y libcups2-dev libasound2-dev libfreetype6-dev libxtst-dev libxrender-dev

# Hack to get around UID mismatch
RUN for i in $(seq 1000 1010); do useradd builder$i -m -u $i ; done
