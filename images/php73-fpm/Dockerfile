FROM php:7.3-fpm
LABEL maintainer="jiangang.xiao@travel-easy.com"
# 官方默认安装的扩展
# Core
# ctype
# curl
# date
# dom
# fileinfo
# filter
# ftp
# hash
# iconv
# json
# libxml
# mbstring
# mysqlnd
# openssl
# pcre
# PDO
# pdo_sqlite
# Phar
# posix
# readline
# Reflection
# session
# SimpleXML
# sodium
# SPL
# sqlite3
# standard
# tokenizer
# xml
# xmlreader
# xmlwriter
# zlib

# Core 自带的可以使用docker-php-ext-install安装
# 有些需要使用pecl安装
# RUN sed -i 's#http://deb.debian.org#https://mirrors.aliyun.com#g' /etc/apt/sources.list; \
RUN apt-get update -y; \
    apt-get install -y \
        libssl-dev \
        libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
        libmemcached-dev \
        libzip-dev \
        zip \
        libmagickcore-dev libmagickwand-dev \
        libzookeeper-mt-dev \
        xvfb libfontconfig wkhtmltopdf; \
    # bcmath
    docker-php-ext-install bcmath;\
    # zip
    docker-php-ext-configure zip --with-libzip; \
    docker-php-ext-install zip; \
    # opcache
    docker-php-ext-install opcache; \
    # pdo_mysql
    docker-php-ext-install pdo_mysql; \
    # mysqli
    docker-php-ext-install mysqli; \
    # sockets
    docker-php-ext-install sockets; \
    docker-php-ext-install sysvmsg sysvsem sysvshm; \
    # GD
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/; \
    docker-php-ext-install -j$(nproc) gd; \
    # memcached
    pecl install memcached; \
    docker-php-ext-enable memcached; \
    # zookeeper
    pecl install zookeeper-1.0.0; \
    docker-php-ext-enable zookeeper; \
    # redis
    pecl install redis; \
    docker-php-ext-enable redis; \
    # imagick
    pecl install imagick;\
    docker-php-ext-enable imagick;\
    # swoole
    pecl install -D 'enable-sockets="no" enable-openssl="yes" enable-http2="yes" enable-mysqlnd="no"' swoole-4.5.9; \
    docker-php-ext-enable swoole; \
    rm -r /var/lib/apt/lists/*