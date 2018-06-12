FROM centos

COPY Atlas-2.2.1.el6.x86_64.rpm /tmp
RUN yum install epel-release -y && yum clean all && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && rpm -ivh /tmp/Atlas-2.2.1.el6.x86_64.rpm && rm /tmp/Atlas-2.2.1.el6.x86_64.rpm && useradd -r -M mysql
COPY mysql-atlas.cnf /usr/local/mysql-proxy/conf/mysql-atlas.cnf 

EXPOSE 3306

CMD ["/usr/local/mysql-proxy/bin/mysql-proxyd","mysql-atlas","start"]
