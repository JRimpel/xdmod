FROM rockylinux:8

RUN dnf update && dnf -y install \
        httpd \
        mariadb mariadb-server\
        libreoffice-writer\
        chromium-headless\
        librsvg\
        perl-Image-Exiftool\
        cronie\
        logrotate\
        sendmail\
        jq

RUN dnf module -y reset php && dnf module install php:7.4
RUN dnf install -y epel-release && php make libzip-devel php-pear php-devel \
                                        mariadb-server mariadb

RUN dnf module -y reset nodejs && dnf module -y install nodejs:16
RUN pecl install mongodb-1.18.1 && echo "extension=mongodb.so" > /etc/php.d/40-mongodb.ini
RUN sed -i 's/.*date.timezone[[:space:]]*=.*/date.timezone = UTC/' /etc/php.ini
 
RUN dnf install https://github.com/ubccr/xdmod/releases/download/v11.0.3-2/xdmod-11.0.3-2.el8.noarch.rpm

