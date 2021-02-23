FROM codesignal/ubuntu-base:new

# Following installation steps from https://cran.r-project.org/bin/linux/ubuntu/
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 51716619E084DAB9 \
  && echo "deb https://cloud.r-project.org/bin/linux/ubuntu focal-cran40/" >> /etc/apt/sources.list \
  && add-apt-repository -y ppa:marutter/rrutter4.0 \
  && add-apt-repository -y ppa:c2d4u.team/c2d4u4.0+ \
  && apt-get update \
  && apt-get install -y --no-install-recommends --allow-unauthenticated \
    r-base \
    r-base-dev \
  && apt-get install -y --no-install-recommends \
    r-cran-stringr \
    r-cran-jsonlite \
    r-cran-httr \
    r-cran-dplyr \
    r-cran-magrittr \
    r-cran-data.table \
    r-cran-futile.logger \
    r-cran-rmysql \
    r-cran-rpostgres \
    r-cran-matrixstats \
  && rm -rf /var/lib/apt/lists/*

# Install additional R packages
RUN Rscript -e "install.packages('tryCatchLog')" \
  && Rscript -e "install.packages('GMCM')"

# Get R version
RUN Rscript --version
