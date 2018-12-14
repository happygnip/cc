FROM php:7.0-fpm

COPY phpredis.tar.gz /tmp/phpredis.tar.gz

RUN mkdir -p phpredis \
    && tar -xf /tmp/phpredis.tar.gz -C phpredis --strip-components=1 \
    && rm /tmp/phpredis.tar.gz \
    && ( \
   	cd phpredis \
        && /usr/local/bin/phpize \
	&& ./configure \
	&& make && make install \ 
    ) \
    && rm phpredis -rf \
    && docker-php-ext-enable redis \
    && apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd pdo pdo_mysql mysqli bcmath sockets gettext
