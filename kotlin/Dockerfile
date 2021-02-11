FROM codesignal/java:new

RUN KOTLIN_VERSION=1.4.21 \
    KOTLIN_COMPILER_URL=https://github.com/JetBrains/kotlin/releases/download/v${KOTLIN_VERSION}/kotlin-compiler-${KOTLIN_VERSION}.zip ; \
  apt-get update \
  && apt-get install -y --no-install-recommends zip unzip \
  && wget $KOTLIN_COMPILER_URL -O /tmp/a.zip \
  && unzip /tmp/a.zip -d /opt  \
  && rm /tmp/a.zip \
  && rm -rf /var/lib/apt/lists/*

ENV PATH $PATH:/opt/kotlinc/bin
