FROM ubuntu:16.04
MAINTAINER Grimlock <grimlock@portnumber53.com>

#RUN pacman -Syyu --noconfirm

#RUN pacman -Syu --noconfirm \
#    sudo wget \
#    jre8-openjdk-headless


RUN apt-get update -qqy \
  && apt-get -qqy install \
    wget sudo \
    bzip2 \
    ca-certificates \
    openjdk-7-jre \
    --no-install-recommends && \
    rm -rf /var/lib/apt/lists/*

# Define commonly used JAVA_HOME variable
ENV JAVA_HOME /usr/lib/jvm/java-7-openjdk-armhf
#ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk/

#==========
# Selenium
#==========
RUN mkdir -p /opt/selenium \
  && wget --no-verbose https://selenium-release.storage.googleapis.com/2.53/selenium-server-standalone-2.53.0.jar -O /opt/selenium/selenium-server-standalone.jar


#========================================
# Add normal user with passwordless sudo
#========================================
RUN sudo useradd seluser --shell /bin/bash --create-home \
  && sudo usermod -a -G wheel seluser \
  && echo 'ALL ALL = (ALL) NOPASSWD: ALL' >> /etc/sudoers \
  && echo 'seluser:secret' | chpasswd

#RUN pacman -Scc

# Define default command
CMD ["bash"]

