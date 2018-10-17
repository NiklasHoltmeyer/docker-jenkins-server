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

USER jenkins

EXPOSE 8080
EXPOSE 50000
