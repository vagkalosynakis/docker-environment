FROM composer:2.7.1

FROM php:8.3.7-fpm-alpine3.19

ARG app_mode
ENV $app_mode=${app_mode}

# COPY --chown=www-data:www-data ./src/ /var/www/html

COPY --from=0 /usr/bin/composer /usr/bin/composer

USER www-data

USER root

RUN if [ "$app_mode" = "dev" ]; then \
        apk add --no-cache $PHPIZE_DEPS \
        && apk add --update linux-headers \
        && pecl install xdebug-3.3.2 \        
        && docker-php-ext-enable xdebug \
        && echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
        && echo "xdebug.start_with_request=yes" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
        && echo "xdebug.client_host=host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini; \
    fi
