# Nginx Dockerfile

# Set the base image to Ubuntu
FROM ubuntu:14.04.3

# File Author / Maintainer
MAINTAINER Drew Miller <atm08e@gmail.com>

# System Level Configurations
ENV DEBIAN_FRONTEND noninteractive

# Update the repository and install stable nginx
RUN apt-get update
RUN apt-get install -y nginx git
RUN apt-get autoclean
#RUN echo "\ndaemon off;" >> /etc/nginx/nginx.conf
#RUN chown -R www-data:www-data /var/lib/nginx

# Certs
# WORKDIR /opt
# RUN git clone https://github.com/letsencrypt/letsencrypt.git
# WORKDIR /opt/letsencrypt
# RUN ./letsencrypt-auto --nginx --email atm08e@gmail.com --agree-tos 1 -d localhost

# Custom Config
ADD default /etc/nginx/sites-available/default

# Add static files and change ownership
RUN mkdir -p /opt/app/static
WORKDIR /opt/app/static
ADD static .
#RUN chown -R www-data:www-data /opt/app/static


# Expose Redis port 6379
EXPOSE 80
EXPOSE 443

# Run Nginx Server
ENTRYPOINT  ["nginx", "-g", "daemon off;"]



