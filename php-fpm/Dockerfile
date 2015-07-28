FROM php:5.6-fpm

RUN apt-get update && \
	apt-get upgrade -y -q && \
	apt-get dist-upgrade -y -q \
	&& apt-get -y -q autoclean && \
	apt-get -y -q autoremove && \
	apt-get install -y -q \
		imagemagick

WORKDIR /var/www
EXPOSE 9000
CMD ["php-fpm"]