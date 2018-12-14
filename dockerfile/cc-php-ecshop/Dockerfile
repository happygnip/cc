FROM php:5.6-fpm-mem 
RUN apt-get update && apt-get install -y  libpng-dev libjpeg-dev libgif-dev libfreetype6-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-jif-dir=/usr/include/ \
    && docker-php-ext-install mysqli gd 
COPY php.ini /usr/local/etc/php/ 
