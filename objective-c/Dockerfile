FROM codesignal/ubuntu-base:new

# Set helper env variables
ENV GNUSTEP_UBUNTU_VERSION="ubuntu-20.04-clang-10.0-runtime-2.0"
ENV GNUSTEP_OBJC_BUILD_DIR="gnustep-build/${GNUSTEP_UBUNTU_VERSION}" \
    GNUSTEP_OBJC_BUILD_SCRIPT="GNUstep-buildon-ubuntu2004.sh"
    
# Note: The installation relies on http://wiki.gnustep.org/index.php/GNUstep_under_Ubuntu_Linux 
# And the command "apt-get install gnustep gnustep-devel" doesn't install all necessary libs
# Download GNUstep
RUN git clone https://github.com/plaurent/gnustep-build/ \
    && cd $GNUSTEP_OBJC_BUILD_DIR \
# Remove sudo and make's multithread flag occurrences from building script
    && sed -i 's/sudo -E //g' $GNUSTEP_OBJC_BUILD_SCRIPT \
    && sed -i 's/sudo //g' $GNUSTEP_OBJC_BUILD_SCRIPT \
    && sed -i 's/ -j8//g' $GNUSTEP_OBJC_BUILD_SCRIPT \
# Build Objective C
    && ./${GNUSTEP_OBJC_BUILD_SCRIPT} \
# Cleanup
    && cd ../.. \
    && rm -rf $GNUSTEP_OBJC_BUILD_DIR \
    && rm -rf /var/lib/apt/lists/*

# Set path to shared libraries for Objective C 
ENV LD_LIBRARY_PATH="/root/GNUstep/Library/Libraries:/usr/GNUstep/Local/Library/Libraries:/usr/GNUstep/System/Library/Libraries:${LD_LIBRARY_PATH}"
