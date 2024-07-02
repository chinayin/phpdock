FROM chinayin/nginx:1.24

WORKDIR /var/www

RUN set -eux \
    ## install packages
    && install_packages logrotate openssl bash curl telnet iputils-ping \
    ## Create 'messages' file used from 'logrotate'
    && touch /var/log/messages

COPY logrotate/nginx /etc/logrotate.d/
COPY assets/ /etc/nginx/assets/
COPY conf.d/ /etc/nginx/conf.d/
COPY nginx.conf /etc/nginx/

RUN set -x  \
    && rm /etc/nginx/conf.d/default.conf \
    && mkdir /etc/nginx/vhost

EXPOSE 80 443

ADD ./startup.sh /opt/startup.sh
RUN sed -i 's/\r//g' /opt/startup.sh
CMD ["/bin/bash", "/opt/startup.sh"]
