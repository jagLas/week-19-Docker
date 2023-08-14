FROM drupal:8.9


RUN apt update && apt install -y git && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www/html/themes

# bootstrap is not compatible with the version of drupal
RUN git clone --branch 8.x-3.x --single-branch --depth 1 https://git.drupal.org/project/bootstrap.git \
    && chown -R www-data:www-data bootstrap