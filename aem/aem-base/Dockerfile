FROM centos:7
MAINTAINER Siarhei Kamenchuk

# Java
ENV JAVA_VERSION 8u74
ENV BUILD_VERSION b02

# AEM
ENV CQ_FOREGROUND y
ENV CQ_VERBOSE    y
ENV CQ_NOBROWSER  y
ENV CQ_JVM_OPTS   "-server -Xmx2048M -Xms512M -Xdebug -Xrunjdwp:transport=dt_socket,server=y,address=30303,suspend=n"
ENV AEM_QUICKSTART_FILE AEM_Quickstart.jar
ENV AEM_WORKING_DIR /opt/aem

# Upgrading system
RUN yum -y upgrade && \
    yum -y install wget && \
    yum clean all
    
# Downloading Java
RUN wget --no-cookies --no-check-certificate --header "Cookie: oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/$JAVA_VERSION-$BUILD_VERSION/jre-$JAVA_VERSION-linux-x64.rpm" -O /tmp/jre-8-linux-x64.rpm

# Installing Java
RUN yum -y install /tmp/jre-8-linux-x64.rpm && \
    alternatives --install /usr/bin/java jar /usr/java/latest/bin/java 200000 && \
    rm -rf /tmp/jre-8-linux-x64.rpm

#Copies required build data
COPY $AEM_QUICKSTART_FILE $AEM_WORKING_DIR/$AEM_QUICKSTART_FILE
COPY license.properties $AEM_WORKING_DIR/license.properties

# Extracts AEM
WORKDIR $AEM_WORKING_DIR
RUN java -Xmx2024M -jar $AEM_QUICKSTART_FILE -unpack -r nosamplecontent,local -v

RUN mkdir -p $AEM_WORKING_DIR/crx-quickstart/install
COPY start $AEM_WORKING_DIR/crx-quickstart/bin/start

ENV JAVA_HOME /usr/java/latest

WORKDIR $AEM_WORKING_DIR
