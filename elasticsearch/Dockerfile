ARG ELK_VERSION
FROM elasticsearch:${ELK_VERSION}

ARG TIMEZONE=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && echo ${TIMEZONE} > /etc/timezone;

EXPOSE 9200 9300
