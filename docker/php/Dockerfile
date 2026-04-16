FROM php:8.3-fpm

RUN apt-get update && apt-get install -y --no-install-recommends \
        git \
        unzip \
        libpq-dev \
        libzip-dev \
    && docker-php-ext-install pdo pdo_pgsql pgsql zip opcache \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

COPY --from=composer:2.7 /usr/bin/composer /usr/bin/composer

ARG UID=1000
ARG GID=1000
RUN usermod -u ${UID} www-data && groupmod -g ${GID} www-data

WORKDIR /var/www/html

USER www-data
