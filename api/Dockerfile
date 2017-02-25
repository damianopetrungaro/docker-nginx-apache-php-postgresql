FROM php:apache
WORKDIR /var/www/
COPY ./Dockerfiles/sites-available/api.conf /etc/apache2/sites-available/api.conf
RUN cd /etc/apache2/sites-available && a2dissite *
RUN cd /etc/apache2/sites-available && a2ensite api
RUN a2enmod rewrite
EXPOSE 80