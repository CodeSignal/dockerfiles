FROM codesignal/java:new

ENV GROOVY_VERSION 3.0.7

RUN apt-get update \
  && apt-get install -y --no-install-recommends unzip \
  && cd /tmp \
  && wget http://dl.bintray.com/groovy/maven/apache-groovy-binary-${GROOVY_VERSION}.zip \
  && unzip apache-groovy-binary-${GROOVY_VERSION}.zip \
  && mv groovy-${GROOVY_VERSION} /opt/groovy \
  && rm apache-groovy-binary-${GROOVY_VERSION}.zip \
  && rm -rf /var/lib/apt/lists/*

ENV GROOVY_HOME=/opt/groovy
ENV PATH=$GROOVY_HOME/bin/:$PATH
