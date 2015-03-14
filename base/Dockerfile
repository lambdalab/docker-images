FROM ubuntu:14.04
MAINTAINER zfy0701
dpkg --add-architecture i386
RUN apt-get update
RUN apt-get install -y software-properties-common
RUN \
  echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
  echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections && \
  add-apt-repository -y ppa:webupd8team/java && \
  apt-get update && \
  apt-get install -y oracle-java7-installer

RUN ln -s /usr/lib/jvm/java-7-oracle /usr/lib/jvm/default-java
RUN apt-get install -y curl libcurl3
