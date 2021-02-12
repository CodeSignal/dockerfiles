FROM codesignal/ubuntu-base:new

# install GHC and Cabal
RUN add-apt-repository -y ppa:hvr/ghc \
  && apt-get update \
  && apt-get install -y --no-install-recommends ghc-8.10.2 cabal-install-3.2 libtinfo-dev \
  && rm -rf /var/lib/apt/lists/*

ENV PATH /root/.cabal/bin:/root/.local/bin:/opt/cabal/3.2/bin:/opt/ghc/8.10.2/bin:$PATH

# install additional global packages
RUN cabal update \
  && cabal install aeson --global --lib \
  && cabal install split --global --lib \
  && cabal install network-uri --global --lib \
  && cabal install regex-compat --global --lib \
  && cabal install regex-posix --global --lib
