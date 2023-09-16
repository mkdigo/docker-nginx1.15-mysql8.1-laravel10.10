FROM php:8.2-fpm

WORKDIR /var/www

RUN docker-php-ext-install pdo pdo_mysql bcmath

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN curl -fsSL https://deb.nodesource.com/setup_16.x | bash -
RUN apt-get update
RUN apt-get install -y nodejs
RUN apt-get install -y npm
RUN apt-get install -y git
RUN apt-get install -y zip

# To resolve write permission error
RUN addgroup --gid 1000 laravel
RUN adduser --ingroup laravel --shell /bin/sh laravel
USER laravel

EXPOSE 9000

ENTRYPOINT [ "php-fpm" ]

# After up the containers you need to do
# chown -R www-data:www-data /var/www/storage
# chown -R www-data:www-data /var/www/bootstrap/cache