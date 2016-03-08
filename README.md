#GoPhish Docker Compose
##Running
The docker-compose.yml uses a config.json file to enable HTTPS.

__Download the docker-compose.yml and config.json files into /srv/gophish:__
```
git clone https://github.com/scottg88/gophish-compose.git /srv/gophish
```

Edit the docker-compose.yml file for any environment-specific settings. E.g. update the "volumes" section if you do not like the default locations.

Copy the "admin" and "phish" certificates to /srv/gophish/ (by default) and __update the permissions:__
```
chmod 0600 /srv/gophish/admin.* /srv/gophish/phish.*
```

__Start the container:__
```
docker-compose up -d
```

##Upgrading
Upgrading with Docker Compose, perform the following from the folder holding docker-compose.yml (default: /srv/gophish):

```
docker-compose down
docker-compose pull
docker-compose up -d
```
