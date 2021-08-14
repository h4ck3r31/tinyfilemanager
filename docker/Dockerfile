FROM php:7.4.14-apache-buster

ARG DEBIAN_FRONTEND=noninteractive

RUN curl -sL https://deb.nodesource.com/setup_14.x | bash - \
    && apt-get update && apt-get install -y --no-install-recommends \
        g++ \
        git \
        libc-client-dev \
        libfreetype6-dev \
        libicu-dev \
        libjpeg62-turbo-dev \
        libkrb5-dev \
        libmagickwand-dev \
        libpng-dev \
        libzip-dev \
        msmtp-mta \
        nano \
        net-tools \
        nodejs \
        openssh-client \
        unzip \
        wget \
        zip \
        zlib1g-dev

RUN docker-php-ext-configure gd --with-jpeg -with-freetype \
    && docker-php-ext-configure imap --with-kerberos --with-imap-ssl \
    && docker-php-ext-install -j$(nproc) \
    iconv \
    imap \
    intl \
    zip

ADD entrypoint.sh /entrypoint.sh

CMD [ "/entrypoint.sh" ]
