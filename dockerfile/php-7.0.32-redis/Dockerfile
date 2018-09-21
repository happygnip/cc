FROM happygnip/php-7.0.32:latest 

COPY php.ini /usr/local/php/etc/php.ini
COPY redis.so /usr/local/php/lib/php/extensions/no-debug-non-zts-20151012/
RUN chmod +x /usr/local/php/lib/php/extensions/no-debug-non-zts-20151012/*
EXPOSE 9000

CMD ["/usr/local/php/sbin/php-fpm"]
