FROM php:8.3.8-fpm-alpine3.20

ENV TZ=Europe/Budapest

RUN adduser -u 1000 -s /bin/fish -D phpdocker

WORKDIR /www

COPY --from=composer:2.7.7 /usr/bin/composer /usr/bin/composer

RUN apk update && apk add --no-cache \
    libzip-dev p7zip zip unzip\
    libpng-dev libjpeg-turbo-dev jpegoptim optipng pngquant gifsicle \
    curl \
    oniguruma-dev \
    libxml2-dev \
    tzdata \
    fish

RUN docker-php-ext-configure gd --with-jpeg

RUN docker-php-ext-install  pdo \
                            pdo_mysql \
                            zip \
                            exif \
                            pcntl \
                            gd

USER phpdocker

CMD ["php-fpm"]
