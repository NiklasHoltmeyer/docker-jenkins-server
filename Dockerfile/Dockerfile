FROM jenkins/jenkins:alpine

COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
USER root

RUN apk update && \
    apk upgrade && \     
    apk add ruby make dos2unix maven && \
    dos2unix  /usr/share/jenkins/ref/plugins.txt && \
    apk del dos2unix && \
    rm -rf /usr/share/jenkins/ref/plugins/* && \
    /usr/local/bin/plugins.sh /usr/share/jenkins/ref/plugins.txt

## Quelle:
RUN apk add --no-cache ca-certificates curl openssl git openssh-client docker
COPY docker-entrypoint.sh /usr/local/bin/docker-entrypoint.sh
##RUN chmod +x /usr/local/bin/docker-entrypoint.sh && sh /usr/local/bin/docker-entrypoint.sh
## Ende: https://bitbucket.org/yobasystems/alpine-docker/src/f5a60c5db781/alpine-docker/?at=master

## Quelle: https://github.com/Zenika/alpine-maven/blob/master/jdk8/Dockerfile

ENV MAVEN_VERSION 3.6.0
ENV MAVEN_HOME /usr/lib/mvn
ENV PATH $MAVEN_HOME/bin:$PATH

RUN wget http://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz && \
  tar -zxvf apache-maven-$MAVEN_VERSION-bin.tar.gz && \
  rm apache-maven-$MAVEN_VERSION-bin.tar.gz && \
  mv apache-maven-$MAVEN_VERSION /usr/lib/mvn
  
 ## Ende: https://github.com/Zenika/alpine-maven/blob/master/jdk8/Dockerfile 
 
 RUN apk add --update ffmpeg

USER jenkins

EXPOSE 8080
EXPOSE 50000
