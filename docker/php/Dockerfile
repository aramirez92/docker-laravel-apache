FROM php:8-apache
RUN apt-get update -y && apt-get install -y apache2 libmcrypt-dev openssl libzip-dev zip unzip git
RUN pecl install mcrypt mbstring zip
WORKDIR /var/www/html
COPY apache.conf /etc/apache2/sites-enabled/000-default.conf
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf
# RUN chmod 777 storage/framework -Rf && chmod 777 storage/logs -Rf && chmod 777 bootstrap/cache -Rf
RUN a2enmod rewrite
# RUN composer install --prefer-dist --no-scripts --no-interaction
CMD /etc/init.d/apache2 restart
EXPOSE 80
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
