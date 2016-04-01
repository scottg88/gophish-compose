#GoPhish Docker Compose
This docker-compose recipe runs GoPhish (http://github.com/gophish/gophish) and a MTA (PostFix) for mail delivery from a specific domain.

The MTA is optional if you have your own mail server or are sending directly to the recipient mail servers. Edit the docker-compose.yml to remove the 'mta' container, the link and the dependency.

##Running
The docker-compose.yml uses a config.json file to enable HTTPS.

__Download the docker-compose.yml, config.json and other files into /srv/gophish:__
```
git clone https://github.com/scottg88/gophish-compose.git /srv/gophish
```

Edit the docker-compose.yml file for any environment-specific settings. E.g. update the "volumes" section if you do not like the default locations.

Copy the "admin" and "phish" certificates to /srv/gophish/ (by default) and __update the permissions:__
```
chmod 0600 /srv/gophish/admin.* /srv/gophish/phish.*
```

Copy the .env and .env_secret samples, update permissions on .env_secret:
```
cp .env.sample .env
cp .env_secret.sample .env_secret
chmod 0600 .env_secret
```

Edit the two environment variable files. '.env' has the primary email domain. '.env_secret' has the SMTP authentication credentials.

__Start the container:__
```
docker-compose up -d
```

##Upgrading
Upgrading with Docker Compose, perform the following from the folder holding docker-compose.yml (default: /srv/gophish):

```
docker-compose pull
docker-compose up -d
```
