FROM centos:centos6

RUN rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm \
    && rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm \
    && yum -y --enablerepo=remi,remi-php72 install httpd php php-common \
    && yum -y --enablerepo=remi,remi-php72 install php-pecl-apcu php-cli php-pear php-pdo php-mysqlnd php-pgsql php-pecl-mongodb php-pecl-memcache php-pecl-memcached php-gd php-mbstring php-mcrypt php-xml \
    && yum -y install https://centos6.iuscommunity.org/ius-release.rpm \
    && yum -y install mysql56u mysql56u-server
# RUN echo 'xdebug.remote_port=9004' >> /etc/php.ini \
#     && echo 'xdebug.remote_enable=1' >> /etc/php.ini \
#     && echo 'xdebug.remote_autostart=1' >> /etc/php.ini \
#     && echo 'xdebug.remote_log=/tmp/xdebug.log' >> /etc/php.ini \
#     && echo 'xdebug.remote_host=docker.for.win.localhost' >> /etc/php.ini \
#     && sed -i -e "s/#ServerName/ServerName/g" /etc/httpd/conf/httpd.conf
COPY ./recruit.conf /etc/httpd/conf.d/
ENTRYPOINT /etc/init.d/mysqld start \
    && /etc/init.d/httpd start \
    && tail -f /dev/null
