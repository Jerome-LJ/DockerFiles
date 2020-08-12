FROM php:7.4.9-fpm-alpine

COPY ./conf/php.ini /usr/local/etc/php/

ENV SWOOLE_VERSION 4.5.2
ENV PHPREDIS_VERSION 5.3.0

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories

RUN cd ~ \
    #安装phpredis
    && wget https://github.com/phpredis/phpredis/archive/$PHPREDIS_VERSION.tar.gz \
    && tar -zxvf $PHPREDIS_VERSION.tar.gz \
    && mkdir -p /usr/src/php/ext \
    && mv phpredis-$PHPREDIS_VERSION /usr/src/php/ext/redis \
    && docker-php-ext-install redis \
    #安装swoole
    && apk add libstdc++ libpng-dev \
    && wget https://github.com/swoole/swoole-src/archive/v$SWOOLE_VERSION.tar.gz \
    && tar -zxvf v$SWOOLE_VERSION.tar.gz \
    && mkdir -p /usr/src/php/ext \
    && mv swoole-src-$SWOOLE_VERSION /usr/src/php/ext/swoole \
    && docker-php-ext-install swoole \
    #添加PHP扩展pdo_mysql mysqli pcntl gd
    && docker-php-ext-install pdo_mysql mysqli pcntl gd \
    #安装composer
    && wget https://install.phpcomposer.com/composer.phar \
    && mv composer.phar /usr/bin/composer \
    && chmod +x /usr/bin/composer \
    && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/ \
    #清理安装包
    && rm -rf ~/$PHPREDIS_VERSION.tar.gz ~/v$SWOOLE_VERSION.tar.gz