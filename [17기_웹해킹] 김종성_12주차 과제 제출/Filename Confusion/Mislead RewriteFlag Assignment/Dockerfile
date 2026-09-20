FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive

# Ubuntu 18.04 기본 패키지(Apache 2.4.29) 설치
RUN apt-get update && apt-get install -y \
    apache2 \
    libapache2-mod-php7.2 \
    php7.2 \
    && rm -rf /var/lib/apt/lists/*

RUN a2enmod rewrite

COPY httpd.conf /etc/apache2/sites-available/000-default.conf
COPY upload/ /var/www/html/upload/

RUN chown -R www-data:www-data /var/www/html && \
    chmod -R 755 /var/www/html

EXPOSE 80
CMD ["apachectl", "-D", "FOREGROUND"]