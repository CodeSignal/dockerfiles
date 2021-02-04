FROM codesignal/ubuntu-base:new

RUN add-apt-repository -y ppa:ubuntu-toolchain-r/test \
  && apt-get update \
  && apt-get install -y --no-install-recommends \
    libcurl4-openssl-dev \
# Installing G++ 8.x version from the ppa
    g++-8 \
    gcc-8 \
# Install GNU Fortran 8
    gfortran-8 \
# Additional C++ dependencies
    libssl-dev \
    libjsoncpp-dev \
    libboost-all-dev \
# Cpprestsdk
    libcpprest-dev \
# Required for Catch 2
    git \
    cmake \
# Install Catch 2
  && git clone https://github.com/catchorg/Catch2.git -b v2.13.2 \
  && cd Catch2 \
  && cmake -Bbuild -H. -DBUILD_TESTING=OFF \
  && cmake --build build/ --target install \
# Clean up
  && apt-get remove -y git cmake \
  && cd .. \
  && rm -rf Catch2/ \
  && rm -rf /var/lib/apt/lists/*
