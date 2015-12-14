keystone-docker
=======
## Summary
Scaleable docker infrastructure for keystone.js. Includes ubuntu base docker containers with nginx/mongodb/nodejs installed respectively. Images are quite large at this moment and "npm install" will barf a little on optional dependencies, but the keystone application doesn't seem effected.


## How To
Prerequisites:
* docker
* docker-composer

To Run:
* cd keystone-docker
* docker-composer up or ./dev_up.sh

To Debug:
* Use build.sh, start.sh for individual dockers

Other:
* Application code is installed at: /opt/app
* Statics accessible at nginx/static/ and served from /opp/app/static

## TODO
* npm install fails on some optional dependencies. Silence/Fix these warnings
* Certs and API Keys integration (https://vaultproject.io/)
* Production tweaks to nginx, mongo, and node
* HA for App servers
* Make sure overlay FS is being used
* Switch to different base image (Alpine, busybox)
* Custom con fig for mongo
