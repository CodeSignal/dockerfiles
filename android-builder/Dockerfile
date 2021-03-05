# We can't use codesignal/java as a base image
# See https://github.com/CodeSignal/dockerfiles/pull/174#issuecomment-653254590
FROM codesignal/ubuntu-base:new

# Install some dependencies
RUN dpkg --add-architecture i386 \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
       expect wget unzip libc6-i386 lib32stdc++6 lib32gcc1 lib32ncurses5 lib32z1 \
    && rm -rf /var/lib/apt/lists/*

# Install java 8, we can't use newer java versions (https://developer.android.com/studio/write/java8-support)
RUN apt-get update \
    && apt-get install -y openjdk-8-jdk-headless \
    && rm -rf /var/lib/apt/lists/*

# Install Android SDK
RUN cd /opt \
    && wget --output-document=android-sdk.zip --quiet \
    https://dl.google.com/android/repository/sdk-tools-linux-4333796.zip \
    && unzip android-sdk.zip -d /opt/android-sdk \
    && rm -f android-sdk.zip

# Setup environment
ENV ANDROID_HOME /opt/android-sdk
ENV PATH ${PATH}:${ANDROID_HOME}/tools/bin:${ANDROID_HOME}/platform-tools

# Install the platform tools and the SDK tools
RUN echo yes | sdkmanager "platform-tools" \
    "platforms;android-30" \
    "platforms;android-29"

# Install recent versions of build tools
RUN echo yes | sdkmanager "platform-tools" \
    "build-tools;30.0.0" \
    "build-tools;29.0.3" "build-tools;29.0.2"
