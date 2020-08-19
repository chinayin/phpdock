ARG PHP_VERSION
FROM chinayin/php-fpm:${PHP_VERSION}

COPY ./php-fpm.ini /usr/local/etc/php/conf.d

RUN set -eux \
    && apt-get update \
    && apt-get upgrade -y \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /var/www
