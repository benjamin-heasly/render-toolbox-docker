FROM ninjaben/render-toolbox-docker-mitsuba:latest

MAINTAINER Ben Heasly <benjamin.heasly@gmail.com>

### pbrt dependencies
RUN apt-get update \
    && apt-get install -y \
    bison \
    build-essential \
    flex \
    git \
    gsl-bin \
    libgsl0-dev \
    libpng12-dev \
    libjpeg-dev \
    libilmbase-dev \
    libopenexr-dev \
    && apt-get clean \
    && apt-get autoclean \
    && apt-get autoremove

### build and install PBRT
WORKDIR /pbrt
RUN git clone https://github.com/ydnality/pbrt-v2-spectral.git
WORKDIR /pbrt/pbrt-v2-spectral/src
RUN make

### make a script for running PBRT
WORKDIR /usr/local/bin
RUN echo '/pbrt/pbrt-v2-spectral/src/bin/pbrt $@' > pbrt \
    && chmod +x pbrt
