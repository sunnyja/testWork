FROM php:7.4-fpm

WORKDIR /app

RUN apt-get update

RUN docker-php-ext-install mysqli

COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/bin/

RUN install-php-extensions xdebug

RUN docker-php-ext-enable xdebug

RUN install-php-extensions zip

COPY conf.d/* $PHP_INI_DIR/conf.d/

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

CMD ["php-fpm"]