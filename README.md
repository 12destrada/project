FROM ubuntu:18.04

RUN apt-get update

RUN apt-get -y install apache2

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data

ENV APACHE_PID_FILE /var/run/apache2/apache2.pid
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_LOG_DIR /var/log/apache2

RUN mkdir -p /var/www/html
RUN mkdir -p /var/run/apache2
RUN mkdir -p /var/lock/apache2

COPY index.html /var/www/html

EXPOSE 80:80

CMD ["/usr/sbin/apache2", "-D", "FOREGROUND"]
