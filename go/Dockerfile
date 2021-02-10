FROM codesignal/ubuntu-base:new

RUN apt-get update \
    && add-apt-repository -y ppa:longsleep/golang-backports \
    && apt-get update \
    && apt-get install -y --no-install-recommends golang-go \
    && rm -rf /var/lib/apt/lists/*
