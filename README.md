# backend-deployment

Is deployed using dockerized images and docker-compose

## services deployed

1. Nginx proxy with frontend app inside

2. Backend API service on route /api/v1

3. MongoDB accessible locally

4. SSL certificate

5. web-scrapping service

```bash
# Run all - !!!!ONLY ONCE!!! -> in root directory of the repository

# first in file nginx.conf comment SSL server section to generate first SSL certificate
# server {
#    listen 443 ssl;
#    # ...
#}

# Run the nginx proxy service (within compose) - for the certbot to be able to generate cert
$ docker-compose up -d

# Now generate the initial certificate
# You should replace example-email@example.com with your email address.
# This command will obtain the certificate and store it in the ./certbot/conf directory.
$ docker-compose run --rm --entrypoint "\
  certbot certonly --webroot -w /var/www/certbot \
    -d factcheck.fel.cvut.cz --email example-email@example.com --agree-tos --no-eff-email --force-renewal" certbot

# Now after succefully generated SSL certificate, uncomment back nginx.conf to the original state

# Shutdown the whole docker-compose, so it uses updated config file
$ docker-compose down

# Now run all the containers - they will use HTTPS now
$ docker-compose up -d
```
