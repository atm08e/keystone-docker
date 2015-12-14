keystone-docker
=======
# Summary
Scaleable docker infrastructure for keystone.js. Uses ubuntu 14.04.3 base image with nginx/mongodb/nodejs installed ontop of respectively.

## App Container
* NodeJS version 4.2.3 is installed to /opt/nodejs. 
* keystone-demo is cloned to /opt/app/keystone
* npm install and node keystone

## Nginx Container
* nginx is installed from 14.04.3 repo
* default nginx conf is copied for reverse proxy and static file hosting

 Images are quite large at this moment and "npm install" will barf a little on optional dependencies, but the keystone application doesn't seem effected.

## How To
Prerequisites:
* docker
* docker-composer
* docker-machine running

To Run:
* cd keystone-docker
* docker-composer up or ./dev_up.sh

To Debug:
* Use build.sh, start.sh, ect for individual docker modules

Other:
* Application code is installed at: /opt/app
* Statics accessible at dockerhost/static/ and served from /opp/app/static
* Tested on Fedora 22 and OSX 10.10 Yosemite
## TODO
* npm install fails on some optional dependencies. Silence/Fix these warnings
* Certs and API Keys integration (https://vaultproject.io/)
* Production tweaks to nginx, mongo, and node
* HA for App servers
* Make sure overlay FS is being used
* Switch to different base image (Alpine, busybox)
* Custom config for mongo
