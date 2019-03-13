# docker-php-tools

[![GitHub](https://img.shields.io/github/license/gaiaz-iusipov/docker-php-extensions.svg)](https://github.com/gaiaz-iusipov/docker-php-extensions#license)
[![Docker Automated build](https://img.shields.io/docker/cloud/automated/gaiaz/php-tools.svg)](https://cloud.docker.com/repository/docker/gaiaz/php-tools)
[![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/gaiaz/php-tools.svg)](https://cloud.docker.com/repository/docker/gaiaz/php-tools)
[![Docker Pulls](https://img.shields.io/docker/pulls/gaiaz/php-tools.svg)](https://hub.docker.com/r/gaiaz/php-tools/)

:whale: A [Docker](https://www.docker.com/) image that contains prebuilt [PHP](https://hub.docker.com/_/php/) tools.

## Tools

- [Composer](https://getcomposer.org/) - Dependency Manager for PHP
- [CacheTool](http://gordalina.github.io/cachetool/) - Manage cache in the CLI
- [PHP CS Fixer](https://cs.symfony.com/) - A tool to automatically fix PHP Coding Standards issues
- [FOAL](https://github.com/sebastianbergmann/foal/) - A tool to find lines eliminated by OpCache's bytecode optimizer

## Usage

```Dockerfile
FROM php:7.2-cli-alpine

COPY --from=gaiaz/php-tools:7.2-alpine \
    /composer \
    /cachetool \
    /php-cs-fixer \
    /foal \
    /usr/local/bin/

RUN set -xe \
    && COMPOSER_ALLOW_SUPERUSER=1 composer --version \
    && cachetool --version \
    && php-cs-fixer --version \
    && foal --version
```

## License

[MIT](http://opensource.org/licenses/MIT) © [Gaiaz Iusipov](https://github.com/gaiaz-iusipov)
