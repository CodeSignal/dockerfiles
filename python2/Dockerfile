FROM codesignal/ubuntu-base:new

ENV PYTHON_VERSION 2.7.18

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    tk-dev \
    tcl-dev \
    libsqlite3-dev \
    libbz2-dev \
    liblzma-dev \
  && rm -rf /var/lib/apt/lists/*

RUN mkdir temp \
  && cd temp \
  && curl -O https://www.python.org/ftp/python/${PYTHON_VERSION}/Python-${PYTHON_VERSION}.tgz \
  && tar -xvzf Python-${PYTHON_VERSION}.tgz \
  && cd Python-${PYTHON_VERSION} \
  && ./configure \
    --prefix=/opt/python/${PYTHON_VERSION} \
    --enable-shared \
    --enable-ipv6 \
    --enable-unicode=ucs4 \
    LDFLAGS=-Wl,-rpath=/opt/python/${PYTHON_VERSION}/lib,--disable-new-dtags > /dev/null 2>&1 \
  && make > /dev/null 2>&1 \
  && make install > /dev/null 2>&1 \
  && cd .. \
  && curl -O https://bootstrap.pypa.io/2.7/get-pip.py \
  && /opt/python/${PYTHON_VERSION}/bin/python get-pip.py \
  && cd .. \
  && rm -rf temp

ENV PATH /opt/python/${PYTHON_VERSION}/bin:$PATH

# this file is needed for MySql-Python installations
COPY my_config.h /usr/include/mysql
RUN python -m pip install \
  pathlib \
  numpy==1.16.1 \
  scipy==1.2.2 \
  pandas \
  scikit-learn \
  keras \
  nltk==3.4.5 \
  requests \
  configparser \
  mysql-connector-python \
  MySql-Python \
  SQLAlchemy \
  psycopg2 \
  toolz \
  appdirs \
  attrs \
  click \
  toml \
  spacy==2.3.0 \
  matplotlib \
  seaborn \
  pytest \
  pymongo \
  flask \
  flask-sqlalchemy \
  flask-migrate \
  ipywidgets \
  pandas-profiling==1.4.1 \
  plotly \
  tweepy \
  eli5 \
  pdpbox \
  shap==0.27 \
  xgboost \
  basilica \
  gensim \
  tensorflow==2.0.0 \
  timeout_decorator \
  Django \
  && python -m spacy download en_core_web_sm
