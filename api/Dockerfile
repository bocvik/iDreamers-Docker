FROM php:7.3.2-apache

LABEL maintainer="Giorgi Botsvadze bocvik@gmail.com"

ENV APACHE_DOCUMENT_ROOT /var/www/html/public

RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf && \
    sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf && \
\
    mv $PHP_INI_DIR/php.ini-production $PHP_INI_DIR/php.ini && \
    apt-get update && \
    apt-get install -y \
        zlib1g-dev \
        libzip-dev \
        libpng-dev && \
    docker-php-ext-install \
        pdo_mysql \
        exif \
        zip \
        gd && \
    a2enmod rewrite

# Copy composer into image
COPY --from=composer:1.9.1 /usr/bin/composer /usr/bin/composer

WORKDIR /