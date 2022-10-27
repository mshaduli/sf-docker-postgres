FROM php:8.1-fpm
ARG GITHUB_EMAIL
ARG GITHUB_NAME

RUN apt-get update && \
    apt-get install -y --no-install-recommends libssl-dev zlib1g-dev curl git unzip netcat libxml2-dev libpq-dev libzip-dev && \
    pecl install apcu && \
    docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql && \
    docker-php-ext-install -j$(nproc) zip opcache intl pdo_pgsql pgsql && \
    docker-php-ext-enable apcu pdo_pgsql sodium && \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
		
RUN apt-get update && apt-get install apt-file -y && apt-file update && apt-get install vim -y
RUN apt install -y supervisor

WORKDIR /var/www/symfony_docker


RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

#RUN curl -sS https://get.symfony.com/cli/installer | bash
#RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony
RUN apt-get install sudo -y
RUN curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | sudo -E bash
RUN apt install symfony-cli
RUN git config --global user.email ${GITHUB_EMAIL} \ 
    && git config --global user.name ${GITHUB_NAME}