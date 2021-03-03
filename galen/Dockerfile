FROM ubuntu:20.04

# Set proper locale
RUN apt-get clean \
    && apt-get update \
    && apt-get install -y locales \
    && locale-gen en_US.UTF-8 \
    && rm -rf /var/lib/apt/lists/*
ENV LANG='en_US.UTF-8' LANGUAGE='en_US:en' LC_ALL='en_US.UTF-8'


#Installing Galen framework and related stuff
RUN apt-get update \
    && apt-get install -y unzip wget bzip2 \
    && wget https://codefightsuserpics.s3.amazonaws.com/galen-ide.zip -P /tmp/ \
    && unzip /tmp/galen-ide.zip -d /tmp \
#Install Firefox 46 version. This exact version is needed for galen-ide
    && cd /usr/local \
    && wget http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/46.0.1/linux-x86_64/en-US/firefox-46.0.1.tar.bz2 \
    && tar -xvjf firefox-46.0.1.tar.bz2 \
    && ln -s /usr/local/firefox/firefox /usr/bin/firefox \
# Cleanup
    && rm /tmp/galen-ide.zip /usr/local/firefox-46.0.1.tar.bz2 \
    && rm -rf /var/lib/apt/lists/*

# Installing xvfb and related stuff
# Install Xvfb init script
ADD xvfb_init /etc/init.d/xvfb
ADD xvfb-daemon-run /usr/bin/xvfb-daemon-run

RUN apt-get update \
    && apt-get -f install \
    && apt-get install -fy xvfb \
    && chmod a+x /etc/init.d/xvfb \
    && update-rc.d xvfb defaults \
    && chmod a+x /usr/bin/xvfb-daemon-run \
    && rm -rf /var/lib/apt/lists/*

# Configuration for noninteractive tzdata installation
ENV DEBIAN_FRONTEND noninteractive
ENV DEBCONF_NONINTERACTIVE_SEEN true
RUN echo 'tzdata tzdata/Areas select Etc' | debconf-set-selections \
    echo 'tzdata tzdata/Zones/Etc select UTC' | debconf-set-selections

RUN apt-get update \
    && apt-get install -y \
    bc \
    sudo \
    software-properties-common \
    curl \
    libcurl4-openssl-dev \
    clang \
    libsigsegv2 \
    libffcall1-dev \
    libreadline5 \
    make \
    libreadline-dev \
    libgtk-3-dev \
    libasound2 \
    libasound2-dev \
    jq \
    dbus-x11

# Install nvm
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
ENV NVM_DIR /root/.nvm

# Install Node with nvm
ENV NODE_VERSION 14.14.0
RUN . $NVM_DIR/nvm.sh && nvm install $NODE_VERSION && nvm alias default $NODE_VERSION && nvm use default
ENV PATH $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH
ENV NODE_PATH=$NVM_DIR/versions/node/v$NODE_VERSION/lib/node_modules

#grab oracle java (auto accept licence)
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        openjdk-11-jdk \
        libjackson2-core-java \
        libjackson2-databind-java \
        libmariadb-java \
        maven \
    && rm -rf /var/lib/apt/lists/*

ENV CLASSPATH=/usr/share/java/*:$CLASSPATH

#Installing Galen framework and related stuff
RUN cd /tmp/galen-ide \
    && . /tmp/galen-ide/assembleAndInstall.sh


ENV DISPLAY :99
    