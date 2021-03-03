FROM codesignal/ubuntu-base:new

RUN apt-get update \
    && wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb \
    && dpkg -i erlang-solutions_1.0_all.deb \
    && apt-get update \
#Install Erland and High-Performance Erlang Project compiler
    && apt-get install -y --no-install-recommends erlang erlang-base-hipe \
# Cleanup
    && rm erlang-solutions_1.0_all.deb \
    && rm -rf /var/lib/apt/lists/*

