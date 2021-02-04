FROM codesignal/ubuntu-base:new

RUN add-apt-repository -y ppa:linuxuprising/java \
    && apt-get update \
    && echo oracle-java15-installer shared/accepted-oracle-license-v1-2 select true | /usr/bin/debconf-set-selections \
    && apt-get install -y --no-install-recommends \
        oracle-java15-installer \
        oracle-java15-set-default \
        libmysql-java \
        maven \
    && rm -rf /var/lib/apt/lists/*

# install gradle
RUN apt-get update \
    && apt-get install -y --no-install-recommends unzip \
    && wget https://services.gradle.org/distributions/gradle-6.7-bin.zip -P /opt/ \
    && unzip /opt/gradle-6.7-bin.zip -d /opt/gradle \
    && apt-get remove -qq -y unzip \
    && apt-get autoremove -qq -y \
    && apt-get autoclean \
    && rm /opt/gradle-6.7-bin.zip \
    && rm -rf /var/lib/apt/lists/*

# install maven
RUN wget https://www-us.apache.org/dist/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz -P /opt/ \
    && mkdir /opt/maven \
    && tar -xzf /opt/apache-maven-3.6.3-bin.tar.gz -C /opt/maven --strip-components 1 \
    && apt-get autoremove -qq -y \
    && apt-get autoclean \
    && rm /opt/apache-maven-3.6.3-bin.tar.gz \
    && rm -rf /var/lib/apt/lists/*

#install javafx
RUN apt-get update \
    && apt-get install -y --no-install-recommends unzip \
    && wget https://download2.gluonhq.com/openjfx/11.0.2/openjfx-11.0.2_linux-x64_bin-sdk.zip -P /opt/ \
    && unzip /opt/openjfx-11.0.2_linux-x64_bin-sdk.zip -d /opt/javafx \
    && apt-get remove -qq -y unzip \
    && apt-get autoremove -qq -y \
    && apt-get autoclean \
    && rm /opt/openjfx-11.0.2_linux-x64_bin-sdk.zip \
    && rm -rf /var/lib/apt/lists/*

ENV CLASSPATH=/usr/share/java/*:$CLASSPATH \
    M2_HOME=/opt/maven \
    MAVEN_HOME=/opt/maven \
    PATH_TO_FX=/opt/javafx/javafx-sdk-11.0.2/lib \
    JAVA_HOME=/usr/lib/jvm/java-15-oracle \
    PATH=$M2_HOME/bin:/opt/gradle/gradle-6.7/bin:$PATH \
    JACKSON_VERSION='2.12.1'

# download dependencies from maven repository with build.gradle script
COPY build.gradle /usr/share/java/build.gradle
RUN cd /usr/share/java \
    && gradle download \
    && rm build.gradle
