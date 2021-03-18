FROM php:7.4-fpm

# Updating and installing some dependences
# TODO remove suggested packages.
RUN apt-get update && \
    apt-get install --no-install-recommends -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libmcrypt-dev \
    libxslt-dev \
    libicu-dev \
    libmemcached-dev \
    zlib1g-dev \
    libzip-dev \
    libmagickwand-dev \
    libmagickcore-dev \
    msmtp \
    git \
    nano \
    gnupg \
    cron \
    unzip \
    zip \
    libwebp-dev \
    libsodium-dev && \
    curl -sL https://deb.nodesource.com/setup_14.x | bash - && \
    apt-get install -y nodejs && \
    docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp && \
    docker-php-ext-install \
    bcmath \
    pdo_mysql \
    xsl \
    intl \
    zip \
    soap \
    gd \
    sockets \
    opcache \
    xmlwriter \
    simplexml && \
    apt-get clean -y && \
    apt-get autoclean -y && \
    apt-get autoremove -y && \
    apt-get purge -y --auto-remove

# Installing pecl PHP modules
RUN pecl install \
    xdebug-3.0.3 \
    imagick-3.4.4 \
    libsodium && \
    docker-php-ext-enable \
    xdebug \
    imagick
        
# Installing extra components
RUN npm install -g grunt-cli && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer --version=1.10.17 && \
    mkdir -p /var/www/.composer && \
    usermod -u 1000 www-data && \
    groupmod -g 1000 www-data && \
    chown -R www-data:www-data /var/www/ && \
    chmod -R g+w /var/www/