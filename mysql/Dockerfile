ARG MYSQL_VERSION
FROM mysql:${MYSQL_VERSION}

ARG CHANGE_SOURCE=true
ARG TIMEZONE=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && echo ${TIMEZONE} > /etc/timezone

COPY my.cnf /etc/mysql/conf.d/my.cnf

RUN chown -R mysql:root /var/lib/mysql/ \
    && chmod 0444 /etc/mysql/conf.d/my.cnf

EXPOSE 3306
CMD ["mysqld"]
