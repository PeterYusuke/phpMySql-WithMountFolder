FROM php:fpm
COPY php.ini /usr/local/etc/php/

# Xdebug install
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

# php module
RUN apt-get update && apt-get install -y \
   zlib1g-dev \
   git \
   libzip* \
   libonig-dev \
   libc-client-dev \
   libkrb5-dev \
   libxml2-dev 

RUN rm -r /var/lib/apt/lists/*

RUN PHP_OPENSSL=yes docker-php-ext-configure imap --with-kerberos --with-imap-ssl \
    && docker-php-ext-install zip pdo_mysql mysqli mbstring imap soap


# composer install
COPY --from=composer /usr/bin/composer /usr/bin/composer
