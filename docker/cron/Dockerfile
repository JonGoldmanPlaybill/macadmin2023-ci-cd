ARG ECR_PHP_URL
FROM ${ECR_PHP_URL:-playbill_php}:${BUILD_NO:-latest}
RUN apt-get install -y cron
RUN touch /var/log/cron.log
COPY ./crontab /etc/cron.d/craft
RUN chmod 0644 /etc/cron.d/craft
RUN crontab /etc/cron.d/craft
COPY ./entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT []
CMD /entrypoint.sh
