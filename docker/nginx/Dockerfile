# Set nginx base image
FROM nginx

COPY ./docker/nginx/site.conf /etc/nginx/conf.d/default.conf
COPY --chown=www-data:www-data ./html /var/www/html

RUN chmod -R 777 /var/www/html/web/cpresources
