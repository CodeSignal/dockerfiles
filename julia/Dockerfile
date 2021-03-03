FROM codesignal/ubuntu-base:new

RUN JULIA_PATH=/usr/local/julia \
    JULIA_VERSION=1.0.1 ;\
  apt-get update \
  && mkdir $JULIA_PATH \
  && curl -sSL "https://julialang-s3.julialang.org/bin/linux/x64/${JULIA_VERSION%[.-]*}/julia-${JULIA_VERSION}-linux-x86_64.tar.gz" -o julia.tar.gz \
  && curl -sSL "https://julialang-s3.julialang.org/bin/linux/x64/${JULIA_VERSION%[.-]*}/julia-${JULIA_VERSION}-linux-x86_64.tar.gz.asc" -o julia.tar.gz.asc \
  && export GNUPGHOME="$(mktemp -d)" \
  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 3673DF529D9049477F76B37566E3C7DC03D6E495 \
  && gpg --batch --verify julia.tar.gz.asc julia.tar.gz \
  && rm -rf "$GNUPGHOME" julia.tar.gz.asc \
  && tar -xzf julia.tar.gz -C $JULIA_PATH --strip-components 1 \
# Cleanup
  && rm -rf /var/lib/apt/lists/* julia.tar.gz*

ENV JULIA_PATH=/usr/local/julia
ENV PATH=$JULIA_PATH/bin:$PATH
