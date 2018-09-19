FROM centos:v1
ENV VERSION=1.13.8

ADD nginx-$VERSION.tar.gz /usr/local/src
WORKDIR /usr/local/src/nginx-$VERSION
RUN buildDeps='make gcc pcre-devel openssl-devel ' \
    && yum install $buildDeps -y \
    && ./configure --prefix=/usr/local/nginx --with-http_stub_status_module \
       --with-http_realip_module --with-http_ssl_module --with-http_addition_module \
       --with-http_gzip_static_module --with-http_v2_module \
    && make && make install && useradd -r -M apache && mkdir /var/log/nginx -p && mkdir /usr/local/nginx/conf/conf.d\
    && ln -s /usr/local/nginx/sbin/nginx /usr/local/sbin/nginx && rm -rf /usr/local/src/nginx-$VERSION && yum remove make gcc -y && yum clean all

#COPY nginx.conf /usr/local/nginx/conf/nginx.conf

EXPOSE 80

CMD ["/usr/local/nginx/sbin/nginx","-g","daemon off;"]
