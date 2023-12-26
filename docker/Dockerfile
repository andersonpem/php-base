ARG PHP_VERSION
FROM --platform=$TARGETPLATFORM php:${PHP_VERSION}-fpm-bookworm

# Install dependencies
RUN apt update -y \
    && apt install unzip \
     libicu-dev \
     libzip-dev \
     git \
     libssh2-1-dev \
     libssh2-1 -y

RUN pecl install ssh2-1.3.1
RUN pecl install redis

RUN docker-php-ext-install pdo_mysql \
    && docker-php-ext-install opcache \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-install zip \
    && docker-php-ext-enable ssh2 \
    && docker-php-ext-enable redis

# Cleanup
RUN rm -rf /var/lib/apt/lists/* \
        && apt clean \
        && apt autoremove -y \
        && rm -rf /tmp/pear