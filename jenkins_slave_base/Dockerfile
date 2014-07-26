FROM lambdalab/base
MAINTAINER zfy0701

RUN apt-get install -y openssh-server
RUN service ssh restart

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]

RUN apt-get install -y python-pip
RUN apt-get install -y ruby2.0; gem install bundle
RUN apt-get install -y ant maven gradle

RUN apt-get install -y curl libcurl3
RUN wget http://repo.scala-sbt.org/scalasbt/sbt-native-packages/org/scala-sbt/sbt/0.13.0/sbt.deb --no-verbose
RUN dpkg -i sbt.deb

RUN apt-get install -y nodejs

RUN apt-get install -y libprotobuf-dev protobuf-compiler
RUN apt-get install -y libboost-dev libboost-test-dev libboost-program-options-dev libevent-dev automake libtool flex bison pkg-config g++ libssl-dev

RUN apt-get install -y mongodb-clients

RUN adduser --quiet jenkins
RUN echo "jenkins:jenkins" | chpasswd
