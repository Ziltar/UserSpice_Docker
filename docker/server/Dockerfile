

FROM php:8.1.1-apache

RUN a2enmod rewrite
RUN apt-get update && apt-get install -y git unzip zip
RUN apt-get update && apt-get install -y libzip-dev zip && docker-php-ext-install zip
RUN docker-php-ext-install pdo pdo_mysql mysqli
WORKDIR /var/www/html

COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/
RUN install-php-extensions gd pdo_mysql bcmath zip intl opcache
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli
COPY --from=composer:2.0 /usr/bin/composer /usr/local/bin/composer
