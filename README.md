![](https://s19.postimg.org/jblfytw9f/laradock-logo.jpg)

[![Build Status](https://travis-ci.org/laradock/laradock.svg?branch=master)](https://travis-ci.org/laradock/laradock) [![GitHub issues](https://img.shields.io/github/issues/laradock/laradock.svg)](https://github.com/laradock/laradock/issues) [![GitHub forks](https://img.shields.io/github/forks/laradock/laradock.svg)](https://github.com/laradock/laradock/network) [![GitHub stars](https://img.shields.io/github/stars/laradock/laradock.svg)](https://github.com/laradock/laradock/stargazers) [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/laradock/laradock/master/LICENSE)

> Use Docker first and learn about it later.

A Docker PHP development environment that facilitates running **PHP** Apps on **Docker**.

[![forthebadge](http://forthebadge.com/images/badges/built-by-developers.svg)](http://zalt.me)

## Documentation

[**Full Documentation Here**](http://laradock.io)

## Credits

**Maintainers:**

- [Mahmoud Zalt](https://github.com/Mahmoudz) @mahmoudz | [Twitter](https://twitter.com/Mahmoud_Zalt) | [Site](http://zalt.me)
- [Bo-Yi Wu](https://github.com/appleboy) @appleboy | [Twitter](https://twitter.com/appleboy)
- [Philippe Trépanier](https://github.com/philtrep) @philtrep
- [Mike Erickson](https://github.com/mikeerickson) @mikeerickson
- [Dwi Fahni Denni](https://github.com/zeroc0d3) @zeroc0d3
- [Thor Erik](https://github.com/thorerik) @thorerik
- [Winfried van Loon](https://github.com/winfried-van-loon) @winfried-van-loon
- [TJ Miller](https://github.com/sixlive) @sixlive
- [Yu-Lung Shao (Allen)](https://github.com/bestlong) @bestlong
- [Milan Urukalo](https://github.com/urukalo) @urukalo
- Join Us.

## License

[MIT License](https://github.com/laradock/laradock/blob/master/LICENSE) (MIT)


# Nginx certbot sertificate

## Get your initial certificate

Run `certbot.sh` in the docker container. It'll see that it didn't fetch any certifcates yet and run the inital setup.

    docker-compose exec nginx /etc/nginx/ssl/certbot.sh -v
    
If you haven't set the `TOS` environment variable `certbot` will ask you to accept their TOS, so be sure to run this command from an interactive shell.

## Update your certificate

`certbot` certificates are only valid for some 90 days. You'll need to refresh them regularly.
The procedure is the same as for the inital step.

Run `certbot.sh` in the docker container. It'll see the existing certificate and run the updater.

    docker-compose exec nginx /etc/nginx/ssl/certbot.sh -v
    
Put this line in your docker-host crontab and run it every month or so.

## Keeping and sharing your certificate

SSL related files are placed in `/etc/letsencrypt/live/<firstdomain>/`. This
directory is recreated with the container, unless you choose to make a volume
and keep this volume.

The `docker-compose.yml` is configured to mount a local `./letsencrypt` directory that
will be populated with all the certbot data.

Edit the `volumes` section `docker-compose.yml` to adapt this to your needs.
