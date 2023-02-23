FROM php:8.1-fpm

# install linux libraries
RUN apt-get update && \
    apt-get install -y zip libzip-dev libpng-dev libjpeg-dev curl libfreetype6-dev libssl-dev libmcrypt-dev libicu-dev

# config gd library
RUN docker-php-ext-configure intl
RUN docker-php-ext-configure gd \
            --prefix=/usr \
            --with-jpeg \
            --with-freetype;

# install php-ext
RUN docker-php-ext-install mysqli pdo pdo_mysql gd zip intl

# create php config
RUN cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini

# install and config xdebug
RUN pecl install xdebug
RUN echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20210902/xdebug.so" >> /usr/local/etc/php/php.ini
COPY ./xdebug/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

# install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer
