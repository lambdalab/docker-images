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
RUN apt-get install -y ant maven

# install build tool - sbt
RUN wget http://repo.scala-sbt.org/scalasbt/sbt-native-packages/org/scala-sbt/sbt/0.13.0/sbt.deb --no-verbose
RUN dpkg -i sbt.deb

RUN wget https://services.gradle.org/distributions/gradle-2.3-bin.zip --no-verbose
RUN unzip gradle-2.3-bin.zip -d /usr/lib
RUN rm gradle-2.3-bin.zip
RUN echo PATH=$PATH:/usr/lib/gradle-2.3/bin >> /etc/environment

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

# help jdk build
RUN apt-get install libcups2-dev libasound2-dev libfreetype6-dev libxtst-dev libxrender-dev

# tools for build android app
RUN wget http://dl.google.com/android/android-sdk_r24.0.2-linux.tgz --no-verbose
RUN tar -xf android-sdk_r24.0.2-linux.tgz -C /usr/lib
RUN echo y | /usr/lib/android-sdk-linux/tools/android update sdk --no-ui -s
RUN echo ANDROID_HOME=/usr/lib/android-sdk-linux >> /etc/environment

RUN adduser --quiet jenkins
RUN echo "jenkins:jenkins" | chpasswd
