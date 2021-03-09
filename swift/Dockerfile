FROM codesignal/ubuntu-base:new

ENV SWIFT_BRANCH=swift-5.3.3-release \
    SWIFT_VERSION=swift-5.3.3-RELEASE \
    SWIFT_PLATFORM=ubuntu20.04 \
    SWIFT_PLATFORM_FOLDER=ubuntu2004

# Install dependencies
RUN apt-get update \
    && apt-get install --no-install-recommends -y \
        binutils \
        git \
        gnupg2 \
        libc6-dev \
        libcurl4 \
        libedit2 \
        libgcc-9-dev \
        libpython2.7 \
        libsqlite3-0 \
        libstdc++-9-dev \
        libxml2 \
        libz3-dev \
        pkg-config \
        tzdata \
        zlib1g-dev \
# Download GPG keys, signature and Swift package, then unpack and cleanup
    && GNUPGHOME="$(mktemp -d)" \
    && SWIFT_ARCHIVE="${SWIFT_VERSION}-${SWIFT_PLATFORM}.tar.gz" \
    && SWIFT_ARCHIVE_SIGNATURE="${SWIFT_ARCHIVE}.sig" \
    && curl -fSsL "https://swift.org/keys/all-keys.asc" | gpg --import - \
    && curl -fSL# "https://swift.org/builds/${SWIFT_BRANCH}/${SWIFT_PLATFORM_FOLDER}/${SWIFT_VERSION}/${SWIFT_ARCHIVE}" -o "${SWIFT_ARCHIVE}" \
    && curl -fSsL "https://swift.org/builds/${SWIFT_BRANCH}/${SWIFT_PLATFORM_FOLDER}/${SWIFT_VERSION}/${SWIFT_ARCHIVE_SIGNATURE}" -o "${SWIFT_ARCHIVE_SIGNATURE}" \
    && gpg --verify "${SWIFT_ARCHIVE_SIGNATURE}" \
    && tar -zxvf "${SWIFT_ARCHIVE}" --directory / --strip-components=1 \
    && rm -r "${GNUPGHOME}" "${SWIFT_ARCHIVE}" "${SWIFT_ARCHIVE_SIGNATURE}" \
    && apt-get -qq -y remove cmake git \
    && apt-get -qq -y autoremove \
    && rm -rf /var/lib/apt/lists/*
