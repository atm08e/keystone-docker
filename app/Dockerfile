# Application Dockerfile

# Set the base image to Ubuntu Stable
FROM ubuntu:15.10

# File Author / Maintainer
MAINTAINER Drew Miller <atm08e@gmail.com>

# System Level Configurations
ENV APP_NAME APP
# Change to RUN <key>=<value> <command>
ENV DEBIAN_FRONTEND noninteractive

# System Dependencies
RUN apt-get update
RUN apt-get install -y build-essential
RUN apt-get install -y git tar python
RUN apt-get autoclean

# Get stable node binaries
ADD https://nodejs.org/dist/v4.2.3/node-v4.2.3-linux-x64.tar.gz .
RUN tar xf node-v4.2.3-linux-x64.tar.gz

# Rename and install
RUN mv node-v4.2.3-linux-x64 /opt/nodejs

# Update path for node/npm bins
ENV PATH=/opt/nodejs/bin:$PATH

# Create Application Folder
RUN mkdir /opt/$APP_NAME

# Change Working Directory to App Folder
WORKDIR /opt/$APP_NAME

# Checkout release branch and mount. Using the keystone-demo as a fake release branch
RUN git clone https://github.com/JedWatson/keystone-demo.git
WORKDIR /opt/$APP_NAME/keystone-demo
RUN npm install

# Copy over Environmental File
# TODO nose doesnt see these files
ADD env /opt/$APP_NAME/keystone-demo/.env
ADD env /.env

# Open 3000 in dev
EXPOSE 3000

# Show IP
RUN ip addr

# Run Node Application
ENTRYPOINT  ["node", "/opt/app/keystone-demo/keystone"]
