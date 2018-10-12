FROM nextcloud:apache

RUN apt-get update && apt-get install -y \
    supervisor \
    ffmpeg \
    libmagickwand-dev \
    libgmp3-dev \
    libc-client-dev \
  && rm -rf /var/lib/apt/lists/* \
  && ln -s "/usr/include/$(dpkg-architecture --query DEB_BUILD_MULTIARCH)/gmp.h" /usr/include/gmp.h \
  && pecl install imagick \
  && docker-php-ext-install bz2 gmp imagick \
  && mkdir /var/log/supervisord /var/run/supervisord

COPY supervisord.conf /etc/supervisor/supervisord.conf

CMD ["/usr/bin/supervisord"]
