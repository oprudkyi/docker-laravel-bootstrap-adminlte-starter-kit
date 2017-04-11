FROM php:7.1-fpm

# this image adds additional extensions to default php image :
# mcrypt zip pdo_mysql opcache gd memcached


MAINTAINER Oleksii Prudkyi <oleksii.prudkyi@gmail.com>

RUN apt-get update -yqq \
		&& buildDeps=" \
			libmemcached-dev  \
			libz-dev  \
			libpq-dev  \
			libjpeg-dev  \
			libpng12-dev  \
			libfreetype6-dev  \
			libmcrypt-dev \
        " \
        && doNotUninstall=" \
                libmemcached11 \
                libmemcachedutil2 \
				libfreetype6 \
				libhashkit2 \
				libjpeg62-turbo \
				libmcrypt4 \
				libpng12-0 \
				libpq5 \
        " \
		&& apt-get install -y zip bzip2 wget tar less $buildDeps --no-install-recommends \
        && rm -r /var/lib/apt/lists/* \
        \
		&& docker-php-ext-install mcrypt zip pdo_mysql opcache \
		&& docker-php-ext-configure gd  \
				--enable-gd-native-ttf  \
				--with-jpeg-dir=/usr/lib  \
				--with-freetype-dir=/usr/include/freetype2 &&  \
				docker-php-ext-install gd \
		&& pecl install memcached \
		&& docker-php-ext-enable memcached \
		&& rm -rf /tmp/pear \
		\
        && apt-mark manual $doNotUninstall \
        && apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps
