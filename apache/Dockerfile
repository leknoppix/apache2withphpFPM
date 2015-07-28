FROM    ubuntu
MAINTAINER PascalCanadas "leknoppix@users.noreply.github.com"
ENV DEBIAN_FRONTEND noninteractive
 
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
 
# Depots, mises a jour et installs
RUN apt-get update && \
	apt-get upgrade -y -q && \
	apt-get dist-upgrade -y -q \
	&& apt-get -y -q autoclean && \
	apt-get -y -q autoremove && \
	apt-get install -y -q \
		apache2 \
		vim
 
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf && \
    sed -i "s/AllowOverride None/AllowOverride All/g" /etc/apache2/apache2.conf
 
RUN apt-get install -y -q apache2-mpm-worker apache2-mpm-event
 
RUN apt-get install -y -q libapache2-mod-fcgid
 
RUN a2dismod mpm_prefork
 
RUN a2enmod rewrite && \
 	a2enmod proxy && \
 	a2enmod proxy_fcgi
 
RUN a2enmod actions alias
 
EXPOSE 80
 
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]