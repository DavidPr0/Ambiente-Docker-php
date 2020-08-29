FROM php:5.6-fpm

RUN apt-get update && apt-get install -y --allow-unauthenticated \
    gnupg \
    libcurl4-openssl-dev \
    libzip-dev \
    git \
    sendmail \
    && docker-php-ext-install pdo pdo_mysql mysql \
    && docker-php-ext-install tokenizer \
    && docker-php-ext-install curl \
    && docker-php-ext-install zip \
    && pecl install intl; echo -e "\nextension=intl.so" >> /usr/local/etc/php/php.ini

RUN pecl install xdebug-2.5.3 \
    && docker-php-ext-enable xdebug

RUN echo "xdebug.remote_autostart=1" | tee -a /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini > /dev/null && \
    echo "xdebug.remote_enable=1" | tee -a /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini > /dev/null && \
    echo "xdebug.remote_host=host.docker.internal" | tee -a /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini > /dev/null

RUN echo 'memory_limit = 2G ' >> /usr/local/etc/php/php.ini