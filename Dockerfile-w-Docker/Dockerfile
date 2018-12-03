FROM niklasholtmeyer/docker-jenkins-server:latest

USER root

RUN apk update && \
    apk upgrade && \   
    apk --update add \            
            docker \
            py-pip &&\
    pip install docker-compose
    
ENV DOCKER_HOST_URL 127.0.0.1
ENV DOCKER_URL https://registry.hub.docker.com
