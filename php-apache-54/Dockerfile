FROM php:5.4-apache

ARG DOCKER_PHP_EXT_INSTALL
ARG DOCKER_PHP_PECL_INSTALL

# https://hub.docker.com/_/composer/
COPY --from=composer:1.6.5 /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /tmp
ENV COMPOSER_VERSION 1.6.5

# https://github.com/wimg/PHPCompatibility/releases
ENV PHP_COMPATIBILITY_VERSION 8.1.0

ENV APACHE_LOG_DIR logs

COPY override.ini /usr/local/etc/php/conf.d/

COPY bash_profile /root/.bash_profile

COPY . /tmp/.
RUN /tmp/build.sh

RUN wget http://robo.li/robo.phar \
  && chmod +x robo.phar \ 
  && mv robo.phar /usr/local/bin/robo