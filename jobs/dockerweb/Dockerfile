FROM php:7.1.17-apache
LABEL maintainer="Jaivic"

RUN sed -i '/deb.debian.org/debian stretch-updates/d' /etc/apt/sources.list
RUN sed -i '/security.debian.org/debian-security stretch/updates/d' /etc/apt/sources.list
RUN echo 'deb http://archive.debian.org/debian/ stretch main contrib non-free' >> /etc/apt/sources.list
RUN echo 'deb http://archive.debian.org/debian/ stretch-updates main contrib non-free' >> /etc/apt/sources.list
RUN echo 'deb http://archive.debian.org/debian-security/ stretch/updates main contrib non-free' >> /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
        zlib1g-dev \
        libicu-dev \
        libxml2-dev \
        libpq-dev \
        && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
        && docker-php-ext-install pdo pdo_mysql pdo_pgsql zip intl xmlrpc soap opcache \
        && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
        && apt-get install vim -y

COPY  . /var/www/html/
WORKDIR /var/www/html/
