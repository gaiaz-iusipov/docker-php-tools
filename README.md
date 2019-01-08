# docker-php-tools

[![GitHub](https://img.shields.io/github/license/gaiaz-iusipov/docker-php-extensions.svg)](https://github.com/gaiaz-iusipov/docker-php-extensions#license)

:whale: A [Docker](https://www.docker.com/) image that contains prebuilt [PHP](https://hub.docker.com/_/php/) tools.

## Tools

- [Composer](https://getcomposer.org/) - Dependency Manager for PHP
- [CacheTool](http://gordalina.github.io/cachetool/) - Manage cache in the CLI
- [PHP CS Fixer](https://cs.symfony.com/) - A tool to automatically fix PHP Coding Standards issues

## Usage

```Dockerfile
FROM php:7.2-cli-alpine

COPY --from=gaiaz/php-tools:7.2-alpine \
    /composer \
    /cachetool \
    /php-cs-fixer \
    /usr/local/bin/

RUN set -xe \
    && COMPOSER_ALLOW_SUPERUSER=1 composer --version \
    && cachetool --version \
    && php-cs-fixer --version
```

## License

[MIT](http://opensource.org/licenses/MIT) © [Gaiaz Iusipov](https://github.com/gaiaz-iusipov)
