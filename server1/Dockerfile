# Server 1 - Apache
FROM ubuntu:latest

# Set environment variable to skip geographic area question when php is installed.
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y apache2

RUN a2enmod proxy_http

COPY apache-config.conf /etc/apache2/sites-available/000-default.conf

# Install PHP8.x repo
RUN apt-get install -y software-properties-common  --fix-missing  && \
    add-apt-repository ppa:ondrej/php && \
    apt update

# Install PHP 8.3
RUN apt install -y  php8.3 php8.3-cli

COPY index.php /var/www/html/index.php

RUN mkdir -p /var/www/html/about
COPY about.php /var/www/html/about/index.php

# Remove index.html file
RUN rm -f /var/www/html/index.html

EXPOSE 80

CMD ["apache2ctl", "-D", "FOREGROUND"]

