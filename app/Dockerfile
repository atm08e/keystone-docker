# Application Dockerfile

# Set the base image to Ubuntu Stable
FROM ubuntu:14.04

# File Author / Maintainer
MAINTAINER Drew Miller <atm08e@gmail.com>

# System Level Configurations
ENV DEBIAN_FRONTEND noninteractive

# System Dependencies
RUN apt-get update
RUN apt-get install -y build-essential
RUN apt-get install -y git tar python

# Get stable node binaries
ADD https://nodejs.org/dist/v4.2.3/node-v4.2.3-linux-x64.tar.gz .
RUN tar xf node-v4.2.3-linux-x64.tar.gz

# Rename for sanity
RUN mv node-v4.2.3-linux-x64 nodejs

# Update path for node/npm bins
ENV PATH=/nodejs/bin:$PATH

# Create Application Folder
RUN mkdir /opt/app

# Change Working Directory to App Folder
WORKDIR /opt/app

# Checkout release branch and mount. Using the keystone-demo as a fake release branch
RUN git clone https://github.com/JedWatson/keystone-demo.git
WORKDIR /opt/app/keystone-demo
RUN npm install

# Copy over Environmental File
# TODO nose doesnt see these files
ADD env /opt/app/keystone-demo/.env
ADD env /.env

# Open 3000
EXPOSE 3000


# Run Node Application
ENTRYPOINT  ["node", "/opt/app/keystone-demo/keystone"]
