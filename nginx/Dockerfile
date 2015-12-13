# Nginx Dockerfile

# Set the base image to Ubuntu
FROM ubuntu:15.10

# File Author / Maintainer
MAINTAINER Drew Miller <atm08e@gmail.com>

# System Level Configurations
ENV DEBIAN_FRONTEND noninteractive

# Update the repository and install stable nginx
RUN apt-get update
RUN apt-get install -y nginx git
RUN apt-get autoclean
RUN echo "\ndaemon off;" >> /etc/nginx/nginx.conf
RUN chown -R www-data:www-data /var/lib/nginx

# Certs
# WORKDIR /opt
# RUN git clone https://github.com/letsencrypt/letsencrypt.git
# WORKDIR /opt/letsencrypt
# RUN ./letsencrypt-auto --nginx --email atm08e@gmail.com --agree-tos 1 -d localhost

# Custom Config
ADD default /etc/nginx/sites-available/default

# Add static files and change ownership
ADD ../app/static /opp/app/static
RUN chown -R www-data:www-data /opp/app/static


# Echo Logs
#RUN ln -sf /dev/stdout /var/log/nginx/access.log
#RUN ln -sf /dev/stderr /var/log/nginx/error.log

# Expose Redis port 6379
EXPOSE 80
EXPOSE 443

# Run Nginx Server
ENTRYPOINT  ["nginx"]



