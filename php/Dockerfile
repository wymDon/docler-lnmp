FROM php:8-fpm

#安装系统依赖
RUN apt-get update && apt-get install -y \
		libzip-dev

ADD ./extensions/redis-5.3.5.tgz/ /usr/src/redis/

#安装扩展
RUN docker-php-source extract
RUN cp -r /usr/src/redis/redis-5.3.5 /usr/src/php/ext/redis
RUN docker-php-ext-install opcache \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install redis \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install zip
RUN docker-php-source delete

WORKDIR /var/www
CMD [ "php-fpm" ]