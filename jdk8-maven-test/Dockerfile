FROM centos:7

MAINTAINER shunsuke maeda <duck8823@gmail.com>

RUN yum -y update

RUN yum -y reinstall glibc-common && \
    localedef -v -c -i ja_JP -f UTF-8 ja_JP.UTF-8; echo "";
ENV LANG=ja_JP.UTF-8
RUN rm -f /etc/localtime && \
    ln -fs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

RUN yum install -y java-1.8.0-openjdk java-1.8.0-openjdk-devel which wget bzip2 ImageMagick

RUN JAVA_HOME=`readlink $(readlink $(which java)) | sed -e "s/\/jre.*//"`

RUN cd /tmp && \
    curl http://ftp.yz.yamagata-u.ac.jp/pub/network/apache/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz -o apache-maven-3.3.9.tar.gz && \
    tar xvzf apache-maven-3.3.9.tar.gz && \
    mv apache-maven-3.3.9 /usr/local/
ENV PATH $PATH:/usr/local/apache-maven-3.3.9/bin

RUN cd /tmp && \
    wget -q https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2 && \
    bzip2 -dc phantomjs-2.1.1-linux-x86_64.tar.bz2 | tar xvf - && \
    mv phantomjs-2.1.1-linux-x86_64 /usr/local/phantomjs
ENV PATH $PATH:/usr/local/phantomjs/bin
