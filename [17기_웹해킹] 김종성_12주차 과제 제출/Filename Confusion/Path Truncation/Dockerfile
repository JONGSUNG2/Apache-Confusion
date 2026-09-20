FROM httpd:2.4.59

# 커스텀 httpd.conf 파일 복사
COPY httpd.conf /usr/local/apache2/conf/httpd.conf

# 권한 설정
RUN chown -R daemon:daemon /usr/local/apache2/htdocs