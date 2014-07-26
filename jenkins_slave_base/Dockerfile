FROM lambdalab/base
MAINTAINER zfy0701

RUN apt-get install -y openssh-server
RUN service ssh restart

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]

# install python
RUN apt-get install -y python-pip

# install ruby
RUN curl -sSL https://get.rvm.io | bash
RUN echo "source /etc/profile.d/rvm.sh; rvm install ruby-2.0.0-p481; gem install bundle" | bash

# install build tools
RUN apt-get install -y ant maven gradle

# install build tool - sbt
RUN wget http://repo.scala-sbt.org/scalasbt/sbt-native-packages/org/scala-sbt/sbt/0.13.0/sbt.deb --no-verbose
RUN dpkg -i sbt.deb

# install node js
RUN apt-get install -y nodejs

# install proto compiler
RUN apt-get install -y libprotobuf-dev protobuf-compiler

# install thrift
RUN apt-get install -y libboost-dev libboost-test-dev libboost-program-options-dev libevent-dev automake libtool flex bison pkg-config g++ libssl-dev

# install mongo client, easy to test
RUN apt-get install -y mongodb-clients

# scm
RUN apt-get install -y git mercurial subversion

RUN adduser --quiet jenkins
RUN echo "jenkins:jenkins" | chpasswd
