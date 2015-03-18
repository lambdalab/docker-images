FROM lambdalab/build_environment
MAINTAINER zfy0701

# tools for build android app
COPY tools /opt/tools
RUN apt-get install -y expect # used by tools
RUN apt-get install -y libc6:i386 libstdc++6:i386 zlib1g:i386
RUN wget http://dl.google.com/android/android-sdk_r24.0.2-linux.tgz --no-verbose
RUN tar -xf android-sdk_r24.0.2-linux.tgz -C /opt
RUN rm android-sdk_r24.0.2-linux.tgz
ENV ANDROID_HOME /opt/android-sdk-linux
RUN ["/opt/tools/android-accept-licenses.sh", "/opt/android-sdk-linux/tools/android update sdk --no-ui --all"]