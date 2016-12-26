FROM php:7.0

# Install git, the php image doesn't have installed
RUN apt-get update -yqq

RUN apt-get install git curl \
        zip wget tar \
        npm nodejs-legacy ruby ruby-dev \
        libtool \
        automake autoconf \
        libmemcached-dev  \
        libz-dev  \
        libpq-dev  \
        libjpeg-dev  \
        libpng12-dev  \
        libfreetype6-dev  \
        libssl-dev  \
        libxml2-dev \
        libsqlite3-dev \
        fontconfig libicu-dev libfontconfig1 \
        libmcrypt-dev -yqq

# Install php extensions
RUN docker-php-ext-install mcrypt
RUN docker-php-ext-install zip
RUN docker-php-ext-install xml
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-configure gd  \
        --enable-gd-native-ttf  \
        --with-jpeg-dir=/usr/lib  \
        --with-freetype-dir=/usr/include/freetype2 &&  \
        docker-php-ext-install gd 

RUN npm -g install phantomjs-prebuilt

