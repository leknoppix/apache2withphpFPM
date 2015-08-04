FROM php:5.6-fpm
ENV TIMEZONE Europe/Paris

RUN apt-get update &&\
	apt-get upgrade -y -q &&\
	apt-get dist-upgrade -y -q &&\
	apt-get -y -q autoclean &&\
	apt-get -y -q autoremove

RUN apt-get install -y locales

RUN dpkg-reconfigure locales &&\
	locale-gen C.UTF-8 &&\
	/usr/sbin/update-locale LANG=C.UTF-8

RUN echo 'fr_FR.UTF-8 UTF-8' >> /etc/locale.gen && locale-gen

ENV LC_ALL C.UTF-8
ENV LANG fr_FR.UTF-8
ENV LANGUAGE fr_FR.UTF-8

# Timezone
RUN echo $TIMEZONE >> /etc/timezone && dpkg-reconfigure tzdata

RUN apt-get install -y -q imagemagick libpng12-dev libjpeg-dev libpq-dev &&\
	rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr &&\
	docker-php-ext-install gd mbstring pdo pdo_mysql pdo_pgsql

COPY config/php.ini /usr/local/etc/php/conf.d/

WORKDIR /var/www
EXPOSE 9000
CMD ["php-fpm"]