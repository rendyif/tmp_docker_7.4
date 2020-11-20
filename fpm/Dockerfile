FROM php:7.4-fpm

# Arguments defined in docker-compose.yml
##ARG user
##ARG uid

# Install system dependencies
RUN apt-get update && apt-get install -y git curl libpng-dev libonig-dev libxml2-dev zip unzip
# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd
RUN apt-get update
RUN apt-get install -y libzip-dev
RUN docker-php-ext-install zip
# Get latest Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version
RUN rm /etc/localtime
RUN ln -s /usr/share/zoneinfo/Asia/Jakarta /etc/localtime
RUN "date"
#Get Nano
RUN apt-get update
RUN apt-get install -y nano
# Set working directory
WORKDIR /var/www

USER $user
