FROM codesignal/ubuntu-base:new

# Install PHP & dependencies
RUN add-apt-repository ppa:ondrej/php \
  && apt-get -qq -y update \
  && apt-get install -y --no-install-recommends php8.0 \
  && apt-get install -y --no-install-recommends \
    php8.0-curl \
    php8.0-mysql \
    php8.0-xml \
  && rm -rf /var/lib/apt/lists/*

# Install PHPUnit
RUN wget -O phpunit https://phar.phpunit.de/phpunit-9.phar \
  && chmod +x phpunit \
  && mv phpunit /usr/local/bin/phpunit
