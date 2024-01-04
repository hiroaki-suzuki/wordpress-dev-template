FROM wordpress:php8.2-fpm

RUN apt-get update && \
    apt-get install -y git && \
    pecl install xdebug-3.2.2 && \
    docker-php-ext-enable xdebug && \
    apt-get install -y locales && \
    locale-gen ja_JP.UTF-8 && \
    rm -rf /var/lib/apt/lists/*

ENV TZ Asia/Tokyo \
    LANG ja_JP.UTF-8 \
    LANGUAGE ja_JP:ja \
    LC_ALL=ja_JP.UTF-8 \
    COMPOSER_ALLOW_SUPERUSER=1 \
    COMPOSER_HOME=/composer

RUN localedef -f UTF-8 -i ja_JP ja_JP.utf8DX
RUN chown -R www-data:www-data /var/www/*

COPY --from=composer:2.0 /usr/bin/composer /usr/bin/composer