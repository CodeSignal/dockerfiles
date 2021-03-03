FROM codesignal/ubuntu-base:new

#Install Lua
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    make \
    libreadline-dev \
    && curl -R -O http://www.lua.org/ftp/lua-5.3.4.tar.gz \
    && tar zxf lua-5.3.4.tar.gz \
    && rm lua-5.3.4.tar.gz \
    && cd lua-5.3.4 \
    && make linux install \
    && wget http://luajit.org/download/LuaJIT-2.0.5.tar.gz \
    && tar -xvzf LuaJIT-2.0.5.tar.gz \
    && rm LuaJIT-2.0.5.tar.gz \
    && cd LuaJIT-2.0.5 \
    && make \
    && make install \
    && rm -rf /var/lib/apt/lists/*
