FROM codesignal/ubuntu-base:new

ENV DEBIAN_FRONTEND='noninteractive'

RUN apt-get remove -yq --purge \
       mysql-server-5.7 \
       && apt-get autoremove -yq \
       && apt-get autoclean -yq \
       && rm -rf /var/lib/mysql /var/run/mysqld /var/log/mysql

#Installing MySQL
RUN echo "mysql-apt-config	mysql-apt-config/select-server select mysql-8.0" | debconf-set-selections \
    && echo "mysql-apt-config	mysql-apt-config/select-product select OK" | debconf-set-selections \
    && echo "mysql-community-server mysql-community-server/root-pass password root" | debconf-set-selections \
    && echo "mysql-community-server mysql-community-server/re-root-pass password root" | debconf-set-selections \
    && echo "mysql-server mysql-server/lowercase-table-names select Enabled" | debconf-set-selections \
    && wget https://dev.mysql.com/get/mysql-apt-config_0.8.13-1_all.deb -P /tmp/ \
    && dpkg -i /tmp/mysql-apt-config_0.8.13-1_all.deb \
    && rm -rf /tmp/* \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
       debconf-utils \
       libmysqlclient-dev  \
       libpq-dev \
       libpq5 \
       libssl-dev \
       mysql-server \
    && mkdir -p /var/lib/mysql \
    && mkdir -p /var/run/mysqld \
    && mkdir -p /var/log/mysql \
    && chown -R mysql:mysql /var/lib/mysql \
    && chown -R mysql:mysql /var/run/mysqld \
    && chown -R mysql:mysql /var/log/mysql \
# UTF-8 and bind-address
    && sed -i -e "$ a [client]\n\n[mysql]\n\n[mysqld]"  /etc/mysql/my.cnf \
    && sed -i -e "s/\(\[client\]\)/\1\ndefault-character-set = utf8/g" /etc/mysql/my.cnf \
    && sed -i -e "s/\(\[mysql\]\)/\1\ndefault-character-set = utf8/g" /etc/mysql/my.cnf \
    && sed -i -e "s/\(\[mysqld\]\)/\1\ninit_connect='SET NAMES utf8'\ncharacter-set-server = utf8\ncollation-server=utf8_unicode_ci\nbind-address = 0.0.0.0/g" /etc/mysql/my.cnf \
# Clean up
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*
