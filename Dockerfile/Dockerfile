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

## python ( https://github.com/frol/docker-alpine-python2/blob/master/Dockerfile ) ##

RUN apk add --no-cache python && \
    python -m ensurepip && \
    rm -r /usr/lib/python*/ensurepip && \
    pip install --upgrade pip setuptools && \
    rm -r /root/.cache

## python ( https://github.com/frol/docker-alpine-python2/blob/master/Dockerfile ) ende ##

RUN apk add --update --no-cache g++ gcc \
                     cython \
                     cython-dev \
                     build-base \
                     libxml2-dev \
                     alpine-sdk \
                     libxml2-dev \
                     libxslt-dev \
                     python-dev  \
                     py-lxml && \
        pip install lxml bzt

USER jenkins

EXPOSE 8080
EXPOSE 50000
