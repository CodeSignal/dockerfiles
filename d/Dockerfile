FROM codesignal/ubuntu-base:new

RUN apt-get update \
  && apt-get install -y --no-install-recommends libcurl3 \
  && wget http://downloads.dlang.org/releases/2.x/2.079.1/dmd_2.079.1-0_amd64.deb \
  && dpkg -i dmd_2.079.1-0_amd64.deb \
  && rm dmd_2.079.1-0_amd64.deb \
  && rm -rf /var/lib/apt/lists/*
