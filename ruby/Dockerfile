FROM codesignal/ubuntu-base:new

# Install required dependencies for Ruby and ruby-build
# https://github.com/rbenv/ruby-build/wiki#ubuntudebianmint
RUN apt-get -qq update \
    && apt-get install --no-install-recommends -y \
        autoconf \
        bison \
        build-essential \
        libssl-dev \
        libyaml-dev \
        libreadline6-dev \
        zlib1g-dev \
        libncurses5-dev \
        libffi-dev \
        libgdbm3 \
        libgdbm-dev \
        libdb-dev \
        libpq-dev \
    && rm -rf /var/lib/apt/lists/*

# Install ruby-build and build Ruby
RUN git clone https://github.com/rbenv/ruby-build.git \
    && PREFIX=/usr/local ./ruby-build/install.sh \
    && ruby-build 2.7.2 /usr/local/ruby-2.7.2

# Update path to include Ruby
ENV PATH=/usr/local/ruby-2.7.2/bin:$PATH

# Install dependencies
RUN gem install \
    activemodel \
    activerecord \
    activesupport \
    excon \
    faker \
    faraday \
    httparty \
    httpclient \
    json \
    multipart-post \
    mysql2 \
    pg \
    pry \
    rest-client \
    rspec

# Verify the installation
RUN ruby --version
