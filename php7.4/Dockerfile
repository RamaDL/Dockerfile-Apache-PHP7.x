FROM alpine:3

LABEL maintainer="RamaDL ramirodldeveloper@gmail.com" 

WORKDIR /shared

ADD https://repos.php.earth/alpine/phpearth.rsa.pub /etc/apk/keys/phpearth.rsa.pub

RUN echo "https://repos.php.earth/alpine/v3.7"  >> /etc/apk/repositories \
    && mkdir /run/apache2 \
    && addgroup -S httpd \ 
    && adduser -S httpd -G httpd \
    && chown httpd /run/apache2 \
    && chgrp httpd /run/apache2 \
    && apk add --no-cache   apache2 \ 
                            php7.4-apache2 \
                            php7.4

COPY ./httpd.conf /etc/apache2/httpd.conf

EXPOSE 80

CMD ["httpd", "-D", "FOREGROUND"]