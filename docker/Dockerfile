ARG PHP_VERSION
FROM --platform=$TARGETPLATFORM php:${PHP_VERSION}-fpm-bookworm

# Install dependencies for building PHP extensions
RUN apt-get update && apt-get install -y \
        libssh2-1-dev \
        libzip-dev \
        libicu-dev \
        && rm -rf /var/lib/apt/lists/*

# Install PECL extensions
RUN pecl install ssh2-1.3.1 \
    && docker-php-ext-enable ssh2

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql \
    && docker-php-ext-install opcache \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-install zip