# backend-deployment

Is deployed using dockerized images and docker-compose

## services deployed

1. Nginx proxy with frontend app inside

2. Backend API service on route /api/v1

3. MongoDB accessible locally

4. SSL certificate

5. web-scrapping service

<!-- ```bash
# Run !!!!ONLY ONCE!!!
# Run certbot before the deployment - to obtain the initial SSL certificate
# You should replace example-email@example.com with your email address.
# This command will obtain the certificate and store it in the ./certbot/conf directory.
# The certbot service in docker-compose will automatically renew the certificate every 12 hours.
$ docker-compose run --rm --entrypoint "\
  certbot certonly --webroot -w /var/www/certbot \
    -d factcheck.fel.cvut.cz --email example-email@example.com --agree-tos --no-eff-email --force-renewal" certbot
``` -->
