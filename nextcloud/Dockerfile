FROM nextcloud:apache

RUN apt-get update && apt-get install -y \
    supervisor \
    ffmpeg \
    libmagickwand-dev \
    libgmp3-dev \
    libc-client-dev \
    sudo \
  && rm -rf /var/lib/apt/lists/* \
  && ln -s "/usr/include/$(dpkg-architecture --query DEB_BUILD_MULTIARCH)/gmp.h" /usr/include/gmp.h \
  && docker-php-ext-install bz2 gmp \
  && mkdir /var/log/supervisord /var/run/supervisord

COPY supervisord.conf /etc/supervisor/supervisord.conf

ENV NEXTCLOUD_UPDATE=1

CMD ["/usr/bin/supervisord"]
