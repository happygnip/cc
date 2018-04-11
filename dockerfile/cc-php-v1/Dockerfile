FROM centos:v1
ENV VERSION=5.6.31

ADD php-$VERSION.tar.gz /usr/local/src
WORKDIR /usr/local/src/php-$VERSION
RUN buildDeps='make openssl-devel pcre-devel gcc libxml2-devel bzip2 libcurl-devel libjpeg-devel libjpeg libpng-devel \
    freetype-devel libicu-devel glibc-headers gcc-c++ libmcrypt-devel libxslt-devel libxslt libxml2-devel bzip2 m4 autoconf' \
    && yum install $buildDeps -y \
    && ./configure --prefix=/usr/local/php --with-config-file-path=/usr/local/php/etc \
       --enable-fpm --with-fpm-user=apache --with-fpm-group=apache --with-mysql=mysqlnd \
       --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd --with-iconv-dir --with-freetype-dir=/usr/local/freetype \
       --with-jpeg-dir --with-png-dir --with-zlib --with-libxml-dir=/usr --enable-xml \
       --disable-rpath --enable-bcmath --enable-shmop --enable-sysvsem --enable-inline-optimization \
       --with-curl --enable-mbregex --enable-mbstring --with-mcrypt --enable-ftp --with-gd --enable-gd-native-ttf \
       --with-openssl --with-mhash --enable-pcntl --enable-sockets --with-xmlrpc --enable-zip --enable-soap \
       --with-gettext --disable-fileinfo --enable-opcache --enable-intl --with-xsl \
    && make && make install && useradd -r -M apache && mkdir /data/release -p && mkdir /var/log/php -p \
    && rm -rf /usr/local/src/php-$VERSION && yum remove make gcc gcc-c++ autoconf -y && yum clean all \
    && cp /usr/local/php/etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf

#COPY php-fpm.conf /usr/local/php/etc/php-fpm.conf
COPY redis.so /usr/local/php/lib/php/extensions/no-debug-non-zts-20131226/redis.so
COPY ssh2.so /usr/local/php/lib/php/extensions/no-debug-non-zts-20131226/ssh2.so
RUN chmod +x /usr/local/php/lib/php/extensions/no-debug-non-zts-20131226/* 

EXPOSE 9000

CMD ["/usr/local/php/sbin/php-fpm"]
