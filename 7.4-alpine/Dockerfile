FROM php:7.4-cli-alpine as builder

# Installing Composer
RUN curl --silent --show-error \
        https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Installing CacheTool
RUN curl --silent --show-error --output /usr/local/bin/cachetool \
        https://gordalina.github.io/cachetool/downloads/cachetool.phar \
    && chmod +x /usr/local/bin/cachetool

# Installing PHP CS Fixer
RUN curl --silent --show-error --output /usr/local/bin/php-cs-fixer \
        https://cs.symfony.com/download/php-cs-fixer-v2.phar \
    && chmod +x /usr/local/bin/php-cs-fixer

# Installing FOAL
RUN curl --silent --show-error --output /usr/local/bin/foal \
        https://phar.phpunit.de/foal.phar \
    && chmod +x /usr/local/bin/foal

FROM scratch

LABEL maintainer="Gaiaz Iusipov <g.iusipov@gmail.com>"

COPY --from=builder \
    /usr/local/bin/composer \
    /usr/local/bin/cachetool \
    /usr/local/bin/php-cs-fixer \
    /usr/local/bin/foal \
    /
