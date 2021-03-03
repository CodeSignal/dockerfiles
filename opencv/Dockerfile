FROM codesignal/cpp:new

ENV OPENCV_VERSION=4.5.1

RUN add-apt-repository -y ppa:ubuntu-toolchain-r/test \
  && apt-get update \
  && apt-get install -y --no-install-recommends \
# OpenCV required dependencies
    cmake \
    git \
    libgtk2.0-dev \
    pkg-config \
    libavcodec-dev \
    libavformat-dev \
    libswscale-dev \
    unzip \
# OpenCV optional dependencies
    python-numpy \
    libtbb2 \
    libtbb-dev \
    libjpeg-dev \
    libpng-dev \
    libtiff-dev \
    libjasper-dev \
    libdc1394-22-dev \
# Install OpenCV
  && wget "https://github.com/opencv/opencv/archive/${OPENCV_VERSION}.zip" -P /tmp/ \
  && unzip "/tmp/${OPENCV_VERSION}.zip" -d /tmp \
  && cd "/tmp/opencv-${OPENCV_VERSION}" \
  && mkdir build \
  && cd build \
  && cmake -D CMAKE_BUILD_TYPE=Release -D OPENCV_GENERATE_PKGCONFIG=YES -D CMAKE_INSTALL_PREFIX=/usr/local .. \
  && make -j8 \
  && make install \
# Clean up
  && cd \
  && rm -rf "/tmp/${OPENCV_VERSION}.zip" \
  && rm -rf /var/lib/apt/lists/*

ENV PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
