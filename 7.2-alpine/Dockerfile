FROM php:7.2-cli-alpine as builder

# Installing Composer
RUN curl --silent --show-error \
        https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && COMPOSER_ALLOW_SUPERUSER=1 composer --version

# Installing PHP CS Fixer
RUN curl --silent --show-error --output /usr/local/bin/php-cs-fixer \
        https://cs.symfony.com/download/php-cs-fixer-v3.phar \
    && chmod +x /usr/local/bin/php-cs-fixer \
    && php-cs-fixer --version

# Installing FOAL
RUN curl --silent --show-error --location --output /usr/local/bin/foal \
        https://phar.phpunit.de/foal.phar \
    && chmod +x /usr/local/bin/foal \
    && foal --version

FROM scratch

LABEL maintainer="Gaiaz Iusipov <g.iusipov@gmail.com>"

COPY --from=builder \
    /usr/local/bin/composer \
    /usr/local/bin/php-cs-fixer \
    /usr/local/bin/foal \
    /
