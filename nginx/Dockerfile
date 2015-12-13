# Nginx Dockerfile

# Set the base image to Ubuntu
FROM ubuntu:14.04

# File Author / Maintainer
MAINTAINER Drew Miller <atm08e@gmail.com>

# System Level Configurations
ENV DEBIAN_FRONTEND noninteractive


# Update the repository and install stable nginx
RUN \
  apt-get update && \
  apt-get install -y nginx && \
  echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  chown -R www-data:www-data /var/lib/nginx


# Custom Config
ADD default /etc/nginx/sites-available/default

# Echo Logs
RUN ln -sf /dev/stdout /var/log/nginx/access.log
RUN ln -sf /dev/stderr /var/log/nginx/error.log

# Expose Redis port 6379
EXPOSE 80
EXPOSE 443

# Run Nginx Server
ENTRYPOINT  ["nginx"]



