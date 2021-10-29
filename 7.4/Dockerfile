FROM php:7.4-fpm

# Updating and installing some dependences
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
    libcurl4-openssl-dev \
    libonig-dev \
    libsodium-dev && \
    curl -sL https://deb.nodesource.com/setup_14.x | bash - && \
    apt-get install -y nodejs && \
    docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp && \
    docker-php-ext-install \
    bcmath \
    sodium \
    # # ctype \
    # curl \
    # # dom \
    gd \
    # # hash \
    # # iconv \
    intl \
    # mbstring \
    # openssl \
    pdo_mysql \
    # simplexml \
    soap \
    xsl \
    zip \
    sockets \
    opcache \
    exif && \
    # xmlwriter && \
    apt-get clean -y && \
    apt-get autoclean -y && \
    apt-get autoremove -y && \
    apt-get purge -y --auto-remove

# Installing pecl PHP modules
# touch /usr/local/etc/php/php.ini && \
#     pear config-set php_ini /usr/local/etc/php/php.ini && \
RUN pecl install \
    xdebug-3.1.1 \
    imagick-3.4.4 && \
    docker-php-ext-enable \
    xdebug \
    imagick
        
# Installing extra components
RUN npm install -g grunt-cli && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer && \
    mkdir -p /var/www/.composer && \
    usermod -u 1000 www-data && \
    groupmod -g 1000 www-data && \
    chown -R www-data:www-data /var/www/ && \
    chmod -R g+w /var/www/