FROM php:8.3-fpm-alpine

WORKDIR /var/www

# Update and install necessary packages
RUN apk update && apk add --no-cache \
    shadow \
    curl \
    libzip-dev \
    zip \
    unzip \
    bash \
    autoconf \
    gcc \
    g++ \
    make \
    zlib-dev \
    oniguruma-dev \
    libxml2-dev \
    postgresql-dev \
    imagemagick-dev \
    redis \
    sqlite-dev 

# Configure non-root user
RUN groupmod -o -g 1000 www-data && \
    usermod -o -u 1000 -g www-data www-data

# Download script to install PHP extensions and dependencies
ADD https://raw.githubusercontent.com/mlocati/docker-php-extension-installer/master/install-php-extensions /usr/local/bin/

# Make the script executable
RUN chmod uga+x /usr/local/bin/install-php-extensions

# Install PHP extensions
RUN install-php-extensions gd imagick intl mysqli pdo_mysql xsl zip exif pdo_pgsql pgsql gmp bcmath pcntl redis

# Clean up
RUN rm -rf /var/cache/apk/* /tmp/* /var/tmp/*

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

USER www-data

EXPOSE 9000
