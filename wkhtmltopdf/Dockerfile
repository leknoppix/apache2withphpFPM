FROM    debian
MAINTAINER PascalCanadas "leknoppix@users.noreply.github.com"
ENV DEBIAN_FRONTEND noninteractive

# Depots, mises a jour et installs
RUN apt-get update &&\
	apt-get upgrade -y -q &&\
	apt-get dist-upgrade -y -q\
	&& apt-get -y -q autoclean &&\
	apt-get -y -q autoremove &&\
	apt-get install -y -q wget

RUN apt-get update && \
    apt-get install -y \
        xfonts-utils \
        xfonts-base \
        xfonts-75dpi

RUN wget http://download.gna.org/wkhtmltopdf/0.12/0.12.2.1/wkhtmltox-0.12.2.1_linux-jessie-amd64.deb

RUN apt-get install -y -q \
	fontconfig \
	libfontconfig1 \
	libjpeg62-turbo \
	libx11-6 \
	libxext6 \
	libxrender1

RUN dpkg -i wkhtmltox-0.12.2.1_linux-jessie-amd64.deb

RUN rm wkhtmltox-0.12.2.1_linux-jessie-amd64.deb

VOLUME ["/usr/local/bin"]

WORKDIR /usr/local/bin

EXPOSE 5000