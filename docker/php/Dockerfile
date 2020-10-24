FROM php:7.4-fpm-alpine

RUN apk update \
    && apk add  --no-cache libxslt-dev graphviz ttf-ubuntu-font-family rabbitmq-c rabbitmq-c-dev bash git mysql-client curl libzip-dev libmcrypt libmcrypt-dev openssh-client icu-dev \
    libxml2-dev freetype-dev libpng-dev libjpeg-turbo-dev g++ make autoconf \
    && docker-php-source extract \
    && pecl install xdebug redis amqp-1.10.2\
    && docker-php-ext-enable amqp \
    && docker-php-ext-enable xdebug redis \
    && docker-php-source delete \
    && docker-php-ext-install xsl pdo_mysql soap intl zip \
#    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#    && echo "xdebug.remote_port=9000" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#    && echo "xdebug.remote_handler=dbgp" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#    && echo "xdebug.remote_connect_back=0" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer global require hirak/prestissimo:0.3.10 \
        --prefer-dist \
        --update-no-dev \
        --no-suggest \
        --no-interaction \
    && rm -rf /tmp/*

CMD ["php-fpm", "-F"]

WORKDIR /var/www/app
COPY --chown=1000:1000 . /var/www/app
EXPOSE 9000
