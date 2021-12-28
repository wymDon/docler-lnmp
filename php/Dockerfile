FROM php:8-fpm

ADD ./extensions/redis-5.3.5.tgz/ /usr/src/redis/
#安装扩展
RUN docker-php-source extract
RUN cp -r /usr/src/redis/redis-5.3.5 /usr/src/php/ext/redis
RUN docker-php-ext-install opcache \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install redis \
    && docker-php-ext-install mysqli
RUN docker-php-source delete

WORKDIR /var/www
CMD [ "php-fpm" ]