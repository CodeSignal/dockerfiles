FROM codesignal/ubuntu-base:new

# libpng12-0 is required as a dependency for some Mono packages, but cannot be installed by default on Ubuntu 20.
# Fix it using this workaround: https://www.linuxuprising.com/2018/05/fix-libpng12-0-missing-in-ubuntu-1804.html
RUN add-apt-repository -y ppa:linuxuprising/libpng12 \
    && apt-get update \
    && apt-get install -y --no-install-recommends libpng12-0 \
    && rm -rf /var/lib/apt/lists/*

# Install Mono: https://www.mono-project.com/download/stable/#download-lin
RUN apt-get update \
    && apt-get install -y --no-install-recommends gnupg ca-certificates \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF \
    && echo "deb https://download.mono-project.com/repo/ubuntu stable-focal main" | tee /etc/apt/sources.list.d/mono-official-stable.list \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
       mono-mcs \
       mono-devel \
       mono-xsp4 \
       mono-xsp4-base \
       mono-complete \
       mono-vbnc \
       ca-certificates-mono \
       fsharp \
    && rm -rf /var/lib/apt/lists/*

#Additional libs for C#
RUN apt-get update \
    && apt-get install -y --no-install-recommends unzip \
    && wget https://dev.mysql.com/get/Downloads/Connector-Net/mysql-connector-net-8.0.11-noinstall.zip -P /tmp/ \
    && unzip /tmp/mysql-connector-net-8.0.11-noinstall.zip -d /tmp && cd /tmp/v4.5.2 && cp MySql.Data.dll /usr/lib/mono/ && cd /usr/lib/mono/ && gacutil -i MySql.Data.dll -package MySql.Data \
    && wget https://github.com/JamesNK/Newtonsoft.Json/releases/download/12.0.3/Json120r3.zip -P /tmp/ \
    && rm -rf /tmp/Newtonsoft && unzip /tmp/Json120r3.zip -d /tmp/Newtonsoft || : && cd /tmp/Newtonsoft/Bin/net45 && cp Newtonsoft.Json.dll /usr/lib/mono/ && cd /usr/lib/mono/ && gacutil -i Newtonsoft.Json.dll -package Newtonsoft.Json \
    && apt-get -qq -y remove unzip \
    && rm -rf /var/lib/apt/lists/*
