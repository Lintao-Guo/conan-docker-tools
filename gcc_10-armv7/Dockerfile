FROM conanio/gcc10

LABEL maintainer="Luis Martinez de Bartolome <luism@jfrog.com>"

ENV CC=arm-linux-gnueabi-gcc-10 \
    CXX=arm-linux-gnueabi-g++-10 \
    CMAKE_C_COMPILER=arm-linux-gnueabi-gcc-10 \
    CMAKE_CXX_COMPILER=arm-linux-gnueabi-g++-10 \
    STRIP=arm-linux-gnueabi-strip \
    RANLIB=arm-linux-gnueabi-ranlib \
    AS=arm-linux-gnueabi-as \
    AR=arm-linux-gnueabi-ar \
    LD=arm-linux-gnueabi-ld \
    FC=arm-linux-gnueabi-gfortran-10

RUN sudo apt-get -qq update \
    && sudo apt-get install -y --no-install-recommends \
       ".*10.*arm-linux-gnueabi.*" \
    && sudo update-alternatives --install /usr/bin/arm-linux-gnueabi-gcc arm-linux-gnueabi-gcc /usr/bin/arm-linux-gnueabi-gcc-10 100 \
    && sudo update-alternatives --install /usr/bin/arm-linux-gnueabi-g++ arm-linux-gnueabi-g++ /usr/bin/arm-linux-gnueabi-g++-10 100 \
    && sudo update-alternatives --install /usr/bin/arm-linux-gnueabi-gcov arm-linux-gnueabi-gcov /usr/bin/arm-linux-gnueabi-gcov-10 100 \
    && sudo update-alternatives --install /usr/bin/arm-linux-gnueabi-gcov-dump arm-linux-gnueabi-gcov-dump /usr/bin/arm-linux-gnueabi-gcov-dump-10 100 \
    && sudo update-alternatives --install /usr/bin/arm-linux-gnueabi-gcov-tool arm-linux-gnueabi-gcov-tool /usr/bin/arm-linux-gnueabi-gcov-tool-10 100 \
    && sudo rm -rf /var/lib/apt/lists/* \
    && pip install -q conan conan-package-tools --upgrade \
    && conan profile new default --detect \
    && conan profile update settings.arch=armv7 default
