FROM codesignal/ubuntu-base:new

# Installing necessary libraries for puppeteer and fonts to support major charsets (Chinese, Japanese, Arabic, Hebrew, Thai and a few others)
# Note: list of the libs is taken from: https://oofnivek.medium.com/ubuntu-install-puppeteer-bd551d6e5fc1
# Also lib libxshmfence1 is not specified in the article but is also needed
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
      libx11-xcb1 \
      libxcomposite1 \
      libxcursor1 \
      libxdamage1 \
      libxi-dev \
      libxtst-dev \
      libnss3 \
      libcups2 \
      libxss1 \
      libxrandr2 \
      libasound2 \
      libatk1.0-0 \
      libatk-bridge2.0-0 \
      libpangocairo-1.0-0 \
      libgtk-3-0 \
      libgbm1 \
      libxshmfence1 \
      fonts-ipafont-gothic \
      fonts-wqy-zenhei \
      fonts-thai-tlwg \
      fonts-kacst \
      ttf-freefont \
    && rm -rf /var/lib/apt/lists/*

# Note: puppeteer will install chromium browser by its own
RUN npm install -g --unsafe-perm=true \
    puppeteer \
    chai \
    sinon \
    mocha
