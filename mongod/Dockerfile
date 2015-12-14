# Mongod Dockerfile

# Set the base image to Ubuntu
FROM ubuntu:14.04.3

# File Author / Maintainer
MAINTAINER Drew Miller <atm08e@gmail.com>

# System Level Configurations
ENV DEBIAN_FRONTEND noninteractive

# Key Server. Seems trustworthy
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10

# Mongo Preinstall
RUN mkdir -p /data/db

# Get mongo repo and install
RUN echo "deb http://repo.mongodb.org/apt/ubuntu "$(lsb_release -sc)"/mongodb-org/3.0\
  multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list
RUN apt-get update
RUN apt-get install -y mongodb-org
RUN apt-get autoclean

# Custom config TODO
# ADD mongo.conf /etc/blah

# Run Nginx Server
ENTRYPOINT  ["mongod"]
