# Dokku deployment

### Routing and domains

[To enable HTTPS](https://jonathanmh.com/dokku-with-multiple-domains-and-letsencrypt/):

1. `sudo dokku plugin:install https://github.com/dokku/dokku-letsencrypt.git`

2. `dokku config:set --no-restart someapp DOKKU_LETSENCRYPT_EMAIL=jonathan@example.com`

3. `dokku letsencrypt someapp`
