FROM nextcloud:fpm-alpine

RUN set -ex; \
    \
    apk add --no-cache \
      supervisor \
      imagemagick \
      ffmpeg \
      bzip2-dev \
      gmp-dev \
    ; \
    \
    docker-php-ext-install \
      bz2 \
      gmp \
    ;

RUN mkdir -p \
    /var/log/supervisord \
    /var/run/supervisord \
;

COPY supervisord.conf /etc/supervisord.conf

# update nextcloud on startup - default entrypoint only checks for apache and php-fpm
ENV NEXTCLOUD_UPDATE=1

CMD ["/usr/bin/supervisord"]
