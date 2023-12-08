# Server 2 - Apache
FROM ubuntu:latest

# Set environment variable to skip geographic area question when php is installed.
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y apache2

# Install PHP 8.3
RUN apt-get install -y software-properties-common  --fix-missing && \
    add-apt-repository ppa:ondrej/php && \
    apt update

#    apt-get install -y php8.3 php8.3-cli php8.3-common php8.3-mysql php8.3-xml php8.3-xmlrpc php8.3-curl php8.3-gd php8.3-imagick php8.3-cli php8.3-dev php8.3-imap php8.3-mbstring php8.3-opcache php8.3-soap php8.3-zip

RUN apt install -y  php8.3 php8.3-cli


RUN mkdir -p /var/www/html/blog

COPY index.php /var/www/html/blog/index.php

EXPOSE 80

CMD ["apache2ctl", "-D", "FOREGROUND"]

