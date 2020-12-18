FROM php:7.4-fpm-alpine

RUN apk -U upgrade

RUN apk add libzip-dev curl-dev libxml2-dev libpng-dev freetype-dev libjpeg-turbo-dev icu-dev oniguruma-dev libxslt-dev zlib-dev nano

RUN docker-php-ext-install pdo_mysql bcmath intl soap xsl zip sockets \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd
  #&& docker-php-ext-install ctype \
  #&& docker-php-ext-install curl \
  #&& docker-php-ext-install dom \
  #&& docker-php-ext-install hash \
  #&& docker-php-ext-install iconv \ 
  #&& docker-php-ext-install mbstring \
  #&& docker-php-ext-install openssl \
  #&& docker-php-ext-install simplexml \
  #&& docker-php-ext-install libxml

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '572cb359b56ad9ae52f9c23d29d4b19a040af10d6635642e646a7caa7b96de717ce683bd797a92ce99e5929cc51e7d5f') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php --install-dir=/usr/bin --filename=composer
RUN php -r "unlink('composer-setup.php');"