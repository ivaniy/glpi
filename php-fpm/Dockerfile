FROM php:7.2-fpm

RUN apt-get update  && apt-get install -y \
   libldap2-dev \ 
   libc-client-dev \ 
   libkrb5-dev \
   libxml2-dev \
   libpng-dev \
   && pecl install apcu \
   && docker-php-ext-enable apcu \
   && docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu/ \
   && docker-php-ext-install ldap \
   && docker-php-ext-configure imap --with-kerberos --with-imap-ssl \
   && docker-php-ext-install -j$(nproc) imap \
   && docker-php-ext-install xmlrpc \
   && docker-php-ext-install xml \
   && docker-php-ext-install mysqli opcache  \
   && docker-php-ext-install gd \

ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini
