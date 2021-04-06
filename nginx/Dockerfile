FROM nginx:alpine

ARG CHANGE_SOURCE=true
ARG TIMEZONE=Asia/Shanghai
RUN if [ ${CHANGE_SOURCE} = true ]; then \
    sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/' /etc/apk/repositories \
;fi && cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && echo "${TIMEZONE}" > /etc/timezone;

RUN set -x  \
    && apk update && apk upgrade \
    && apk --update add logrotate \
    && apk add --no-cache openssl bash curl \
    && apk add --no-cache busybox-extras \
    ## Create 'messages' file used from 'logrotate'
    && touch /var/log/messages

# Copy 'logrotate' config file
COPY logrotate/nginx /etc/logrotate.d/

COPY nginx.conf /etc/nginx/

# Set upstream conf and remove the default conf
ARG PHP_UPSTREAM_CONTAINER=php-fpm
ARG PHP_UPSTREAM_PORT=9000
ARG PHP72_UPSTREAM_CONTAINER=php-fpm72
ARG PHP72_UPSTREAM_PORT=9002
RUN set -x  \
    && echo "upstream php-upstream { server ${PHP_UPSTREAM_CONTAINER}:${PHP_UPSTREAM_PORT}; }" >> /etc/nginx/conf.d/upstream.conf \
    && echo "upstream php72-upstream { server ${PHP72_UPSTREAM_CONTAINER}:${PHP72_UPSTREAM_PORT}; }" >> /etc/nginx/conf.d/upstream.conf \
    && rm /etc/nginx/conf.d/default.conf \
    && mkdir /etc/nginx/vhost

EXPOSE 80 443
WORKDIR /var/www

ADD ./startup.sh /opt/startup.sh
RUN sed -i 's/\r//g' /opt/startup.sh
CMD ["/bin/bash", "/opt/startup.sh"]
