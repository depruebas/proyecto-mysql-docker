FROM ubuntu:22.04

ARG UID

RUN adduser -u ${UID} --disabled-password --gecos '' devuser

ENV TZ=Europe/Madrid
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update -y \
    && apt-get install -y git acl openssl openssh-client wget zip curl gcc make perl vim htop \ 
    libpng-dev zlib1g-dev libzip-dev libxml2-dev libicu-dev build-essential sudo \
    apache2 php-mysql php-curl php-tidy php-gd php-cli php-pear php-pgsql php-dev libapache2-mod-php \
    php-mbstring php-bcmath apache2-dev net-tools php-ssh2 php-sqlite3 php-intl iproute2 iputils-ping locales \ 
    python3-venv python3-dev libmysqlclient-dev libapache2-mod-wsgi-py3 python3-pip mysql-client \ 
    libpq-dev postgresql-client

RUN apt-get upgrade -y

RUN locale-gen es_ES.UTF-8
RUN echo 'echo "LANG=es_ES" > /etc/default/locale'
ENV LC_ALL=es_ES.UTF-8

RUN adduser devuser sudo
RUN adduser devuser adm

RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

RUN ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/rewrite.load 

RUN chown -R devuser:devuser /var/www/html

# Le decimos que escuche en el puerto 80 para el servidor Web
EXPOSE 80

# y le decimos que al arrancar la maquina ejecute apache2 para que este listo para trabajar.
ENTRYPOINT ["apache2ctl", "-D", "FOREGROUND"]