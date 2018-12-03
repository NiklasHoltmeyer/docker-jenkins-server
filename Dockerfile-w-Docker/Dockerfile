FROM niklasholtmeyer/docker-jenkins-server:latest

USER root

RUN apk update && \
    apk upgrade && \   
    apk --update add \            
            docker \
            py-pip &&\
    pip install docker-compose

