FROM remote-host

COPY ./conf/nginx.repo /etc/yum.repos.d/nginx.repo

RUN yum install -y nginx-1.12.2 openssl --enablerepo=nginx

RUN  yum install -y http://rpms.remirepo.net/enterprise/remi-release-7.rpm
RUN  yum-config-manager --enable remi-php71
RUN  yum install -y                                                             \
    php-fpm                                                               \
    php-cli                                                               \
    php-mysqlnd                                                           \
    php-soap                                                              \
    php-xml                                                               \
    php-zip                                                               \
    php-json                                                              \
    php-mcrypt                                                            \
    php-mbstring                                                          \
    php-zip                                                               \
    php-gd                                                                
RUN yum clean all

EXPOSE 80 443

VOLUME /var/www/html /var/log/nginx /var/log/php-fpm /var/lib/php-fpm

RUN setfacl -R -m u:remote-user:rwx /var/www/html

COPY ./conf/nginx.conf /etc/nginx/conf.d/default.conf

COPY ./bin/start.sh /start.sh

RUN chmod +x /start.sh

CMD /start.sh

