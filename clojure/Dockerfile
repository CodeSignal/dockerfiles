FROM codesignal/java:new

# https://clojure.org/guides/getting_started#_installation_on_linux
RUN CLOJURE_VERSION=1.10.2.774 ;\
  apt-get update \
  && apt-get -y install rlwrap --no-install-recommends \
  && curl -sSL "https://download.clojure.org/install/linux-install-${CLOJURE_VERSION}.sh" -o /tmp/clojure-install.sh \
  && chmod +x /tmp/clojure-install.sh \
  && bash /tmp/clojure-install.sh \
  && rm -rf /tmp/clojure-install.sh \
  # run Clojure to download dependencies
  && clj -e "(clojure-version)" \
  && rm -rf /var/lib/apt/lists/*
