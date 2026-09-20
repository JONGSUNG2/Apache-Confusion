FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

# Apache, PHP-FPM, Apache-PHP proxy 모듈 설치
RUN apt-get update && apt-get install -y \
    apache2 \
    php8.1-fpm \
    curl \
    && rm -rf /var/lib/apt/lists/*

# PHP-FPM 소켓 및 실행 디렉터리 생성
RUN mkdir -p /run/php && chown -R www-data:www-data /run/php

# Apache 필수 모듈 활성화
RUN a2enmod proxy proxy_fcgi rewrite authn_file authz_user authz_core

# 설정 파일 및 소스 코드 복사
COPY httpd.conf /etc/apache2/sites-available/000-default.conf
COPY admin.php /var/www/html/admin.php
COPY .htpasswd /etc/apache2/.htpasswd

EXPOSE 80

# PHP-FPM 실행 후 Apache를 Foreground로 실행
CMD /bin/sh -c "service php8.1-fpm start && apachectl -D FOREGROUND"