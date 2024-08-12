FROM php:fpm-alpine

RUN apk --update add --no-cache nginx icu zlib libpng postgresql-dev

# PHP_CPPFLAGS are used by the docker-php-ext-* scripts
ENV PHP_CPPFLAGS="$PHP_CPPFLAGS -std=c++17"

RUN docker-php-ext-install pdo pdo_mysql \
    mysqli pdo_pgsql pgsql opcache gd \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl

RUN { \
    echo 'opcache.memory_consumption=128'; \
    echo 'opcache.interned_strings_buffer=8'; \
    echo 'opcache.max_accelerated_files=4000'; \
    echo 'opcache.revalidate_freq=2'; \
    echo 'opcache.fast_shutdown=1'; \
    echo 'opcache.enable_cli=1'; \
    } > /usr/local/etc/php/conf.d/php-opocache-cfg.ini

COPY nginx-site.conf /etc/nginx/sites-enabled/default
COPY entrypoint.sh /etc/entrypoint.sh

COPY --chown=www-data:www-data ./www /www

WORKDIR /www

EXPOSE 8000 9000

ENTRYPOINT ["/etc/entrypoint.sh"]
