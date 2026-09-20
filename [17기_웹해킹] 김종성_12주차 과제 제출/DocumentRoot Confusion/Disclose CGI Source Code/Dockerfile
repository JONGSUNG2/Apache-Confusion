FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive

# Apache 및 Perl (CGI 실행용) 설치
RUN apt-get update && apt-get install -y \
    apache2 \
    perl \
    && rm -rf /var/lib/apt/lists/*

# cgi, rewrite 모듈 활성화
RUN a2enmod cgi rewrite

# 설정 파일 및 CGI 스크립트 복사
COPY httpd.conf /etc/apache2/sites-available/000-default.conf
COPY download.cgi /usr/lib/cgi-bin/download.cgi

# 실행 권한 부여
RUN chmod +x /usr/lib/cgi-bin/download.cgi

EXPOSE 80
CMD ["apachectl", "-D", "FOREGROUND"]