FROM php:7.4-fpm

RUN apt-get update \
   && apt-get install -y --no-install-recommends \
       libpq-dev \
       libmemcached-dev \
       libjpeg-dev \
       libpng-dev \
       libfreetype6-dev \
       libwebp-dev \
       libssl-dev \
       libmcrypt-dev \
       curl \
       openssh-server \
       iputils-ping netcat \
       libzip-dev \
   && mkdir /var/run/sshd \
   && docker-php-ext-configure gd \
       --with-jpeg=/usr/include \
       --with-webp=/usr/include \
       --with-freetype=/usr/include \
   && docker-php-ext-install -j$(nproc) \
       opcache \
       gd \
       mysqli \
       pdo_mysql \
       zip \
   && pecl install \
       memcached \
   && docker-php-ext-enable \
       memcached \
   && docker-php-source delete \
   && rm -rf /var/lib/apt/lists/* /tmp/* /var/cache/apt/*

RUN usermod -u 1000 www-data

WORKDIR /var/www/html

EXPOSE 9000

CMD ["/usr/sbin/sshd", "-D"]
CMD ["php-fpm"]