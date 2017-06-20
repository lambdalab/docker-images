FROM lambdalab/base
MAINTAINER lambdalab

ENV LANG en_US.UTF-8

RUN locale-gen en_US.UTF-8

RUN add-apt-repository -y ppa:ondrej/php
RUN add-apt-repository -y ppa:ubuntu-toolchain-r/test
RUN add-apt-repository -y ppa:git-core/ppa 
RUN apt-get update

# install python
RUN apt-get install -y python-pip
RUN pip install -U pip setuptools
RUN apt-get install -y python-dev libxml2-dev libxslt-dev

# install ruby
RUN curl -sSL https://get.rvm.io | bash
RUN echo "source /etc/profile.d/rvm.sh; rvm install ruby-2.0.0-p481; gem install bundle" | bash

# install zip
RUN apt-get install -y zip

# ant, maven
RUN apt-get install -y ant maven

# mercurial/hg
RUN apt-get install -y mercurial meld

# install node js
RUN wget http://nodejs.org/dist/v0.12.2/node-v0.12.2-linux-x64.tar.gz --no-verbose
RUN tar -xf node-v0.12.2-linux-x64.tar.gz -C /opt
RUN rm node-v0.12.2-linux-x64.tar.gz
ENV PATH $PATH:/opt/node-v0.12.2-linux-x64/bin

# install proto compiler
RUN apt-get install -y libprotobuf-dev
#protobuf-compiler
RUN apt-get install -y protobuf-compiler
# RUN wget https://github.com/google/protobuf/releases/download/v3.0.0-beta-3/# protoc-3.0.0-beta-3-linux-x86_64.zip
#RUN unzip protoc-3.0.0-beta-3-linux-x86_64.zip -d /opt/protobuf
#RUN rm protoc-3.0.0-beta-3-linux-x86_64.zip
#ENV PATH $PATH:/opt/protobuf

# install thrift
RUN apt-get install -y libevent-dev automake libtool flex bison pkg-config g++ libssl-dev

# install mongo client, easy to test
RUN apt-get install -y mongodb-clients

# scm 
RUN apt-get install git -y

# php
RUN apt-get install -y php7.0 php7.0-xml php7.0-mbstring

# help jdk build
RUN apt-get install -y libcups2-dev libasound2-dev libfreetype6-dev libxtst-dev libxrender-dev

# install build tool
RUN apt-get install -y build-essential texinfo libtool bc

# install cmake
RUN wget https://cmake.org/files/v3.8/cmake-3.8.1.tar.gz
RUN tar -xf cmake-3.8.1.tar.gz
RUN cd cmake-3.8.1 && ./bootstrap && make && make install
RUN rm -rf cmake-3.8.1*

# install gcc 5
RUN apt-get install -y gcc-5 g++-5 cpp-5 c++-5
RUN update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 1
RUN update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-5 1
# RUN update-alternatives --install /usr/bin/cpp cpp /usr/bin/cpp-5 1
# RUN update-alternatives --install /usr/bin/c++ c++ /usr/bin/c++-5 1

# install intel omp so that it's header could be found by clang
RUN apt-get install -y libiomp-dev

# Hack to get around UID mismatch
RUN for i in $(seq 1000 1010); do useradd builder$i -m -u $i -G sudo,root; done
RUN ln -s /root /home/builder0

RUN echo "%sudo ALL=(ALL) NOPASSWD: /usr/bin/apt-get" >> /etc/sudoers

# Anddroid SDK mount point
ENV ANDROID_HOME /android-sdk-linux
RUN apt-get install -y lib32stdc++6 lib32z1

# install iconv lib
RUN curl https://gist.githubusercontent.com/merqlove/eda0bd9511fce0d319e6efb152f8c68d/raw/33d444fc8536de3ca092efb5823bbfbaeb7c45a3/iconv_install_ubuntu14.sh | sh

# Others to prevent build failed
RUN apt-get install -y doxygen ascii

# TODO: make apt-get need no sudo
