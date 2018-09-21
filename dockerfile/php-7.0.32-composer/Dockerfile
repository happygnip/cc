FROM php-7.0

RUN yum install epel-release -y && yum install composer -y && yum clean all
EXPOSE 9000

CMD ["/usr/local/php/sbin/php-fpm"]
