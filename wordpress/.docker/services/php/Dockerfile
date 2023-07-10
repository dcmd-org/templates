FROM php:8.1.16-fpm

RUN apt update -y &&\
    apt install git -y

RUN curl -sSLf \
    -o /usr/local/bin/install-php-extensions \
    https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions && \
    chmod +x /usr/local/bin/install-php-extensions

RUN install-php-extensions \
    pdo_mysql \
    gd \
    zip \
    gmp \
    exif \
    opcache \
    intl \
    mysqli

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" &&\
    php composer-setup.php &&\
    php -r "unlink('composer-setup.php');" &&\
    mv composer.phar /usr/local/bin/composer

CMD ["php-fpm"]
