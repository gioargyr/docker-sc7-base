#################################
# Base Docker for SC7-Pilot     #
# BigDataEurope, Horizon2020    #
# 				#
# debian:jessie			#
# java:8                        #
# maven 3.0.5		        #
# git 1.9.1			#
# tomcat 8.0.23                 #
# nano				#
#################################


FROM java:8

MAINTAINER Giorgos Argyriou <gioargyr@gmail.com>

ENV PORT 8080
ENV TOMCAT_MAJOR_VERSION 8
ENV TOMCAT_MINOR_VERSION 8.0.23

# INSTALL PREREQUISITIES
RUN apt-get update \
      && apt-get install -y \
         curl \
	 vim \
	 maven \
	 git \
      && apt-get clean \
      && rm -rf /var/lib/apt/lists/*

# INSTALL TOMCAT
RUN wget -q https://archive.apache.org/dist/tomcat/tomcat-${TOMCAT_MAJOR_VERSION}/v${TOMCAT_MINOR_VERSION}/bin/apache-tomcat-${TOMCAT_MINOR_VERSION}.tar.gz && \
    wget -qO- https://archive.apache.org/dist/tomcat/tomcat-${TOMCAT_MAJOR_VERSION}/v${TOMCAT_MINOR_VERSION}/bin/apache-tomcat-${TOMCAT_MINOR_VERSION}.tar.gz.md5 | md5sum -c - && \
    tar zxf apache-tomcat-*.tar.gz && \
    rm apache-tomcat-*.tar.gz && \
    mv apache-tomcat* tomcat

ADD create_tomcat_admin_user.sh /create_tomcat_admin_user.sh
ADD sc7base.sh /sc7base.sh

EXPOSE $PORT
CMD ["/bin/bash", "/sc7base.sh"]
