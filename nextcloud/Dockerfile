FROM nextcloud:apache

RUN apt-get update && apt-get install -y \
    supervisor \
    ffmpeg \
    libgmp3-dev \
    libbz2-dev \
    sudo \
  && rm -rf /var/lib/apt/lists/* \
  && docker-php-ext-install bz2 gmp \
  && mkdir /var/log/supervisord /var/run/supervisord

COPY supervisord.conf /etc/supervisor/supervisord.conf

ENV NEXTCLOUD_UPDATE=1

CMD ["/usr/bin/supervisord"]
