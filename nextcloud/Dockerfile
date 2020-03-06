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

RUN crontab -u www-data -l > www-data.cron && \
    echo "*/10 * * * * /var/www/html/occ preview:pre-generate" >> www-data.cron && \
    crontab -u www-data www-data.cron

# update nextcloud on startup - default entrypoint only checks for apache and php-fpm
ENV NEXTCLOUD_UPDATE=1

CMD ["/usr/bin/supervisord"]
