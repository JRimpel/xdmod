FROM rockylinux:8

RUN dnf module -y reset php && dnf module -y enable php:7.4

RUN dnf install -y epel-release

RUN dnf install -y php make libzip-devel php-pear php-devel \
            mariadb-server mariadb

RUN dnf module -y reset nodejs && dnf module -y install nodejs:16

RUN pecl install mongodb-1.18.1 && echo "extension=mongodb.so" > /etc/php.d/40-mongodb.ini

RUN sed -i '/\[server\]/a sql_mode=' etc/my.cnf.d/mariadb-server.cnf && sed -i 's/.*date.timezone[[:space:]]*=.*/date.timezone = UTC/' /etc/php.ini


RUN dnf install -y https://github.com/ubccr/xdmod/releases/download/v11.0.3-2/xdmod-11.0.3-2.el8.noarch.rpm
CMD ["sleep", "infinity"]

