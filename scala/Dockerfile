FROM codesignal/java:new

RUN apt-get update \
    && wget https://www.scala-lang.org/files/archive/scala-2.12.13.deb \
    && dpkg -i scala-2.12.13.deb \
    && apt-get update \
    && apt-get install -y scala \
    && rm -rf scala-2.12.13.deb  /var/lib/apt/lists/*
