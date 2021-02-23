FROM codesignal/ubuntu-base:new

#Install Dart 1.24.2
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
# Enable HTTPS for apt.
    apt-transport-https \
# Get the Google Linux package signing key.
    && curl https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
# Set up the location of the stable repository.
    # && curl https://storage.googleapis.com/download.dartlang.org/linux/debian/pool/main/d/dart/dart_1.24.3-1_amd64.deb > /etc/apt/sources.list.d/dart_stable.list \
    # && apt-get update \
    && wget https://storage.googleapis.com/download.dartlang.org/linux/debian/pool/main/d/dart/dart_1.24.2-1_amd64.deb \
    && dpkg -i dart_1.24.2-1_amd64.deb \
    && apt-get install -y --no-install-recommends dart=1.24.2-1 \
# Cleanup
    && apt-get remove -qq -y apt-transport-https \
    && rm -rf /var/lib/apt/lists/*



