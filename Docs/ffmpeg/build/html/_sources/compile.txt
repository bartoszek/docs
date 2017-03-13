compiling ffmpeg
================

https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu

Ubuntu 14.04
............

.. code:: tcsh

  add-apt-repository ppa:mc3man/trusty-media
  apt-get update
  apt-get dist-upgrade
  apt-get install ffmpeg

Ubuntu 16.04
............


.. code:: tcsh

  mkdir ~/ffmpeg_sources
  #libx265
  cd ~/ffmpeg_sources
  hg clone https://bitbucket.org/multicoreware/x265
  cd ~/ffmpeg_sources/x265/build/linux
  PATH="$HOME/bin:$PATH" cmake -G "Unix Makefiles" -DCMAKE_INSTALL_PREFIX="$HOME/ffmpeg_build" -DENABLE_SHARED:bool=off ../../source
  make
  make install
  make distclean
  #libfdk-aac
  cd ~/ffmpeg_sources
  wget -O fdk-aac.tar.gz https://github.com/mstorsjo/fdk-aac/tarball/master
  tar xzvf fdk-aac.tar.gz
  cd mstorsjo-fdk-aac*
  autoreconf -fiv
  ./configure --prefix="$HOME/ffmpeg_build" --disable-shared
  make
  make install
  make distclean
  #libvpx
  cd ~/ffmpeg_sources
  wget http://storage.googleapis.com/downloads.webmproject.org/releases/webm/libvpx-1.5.0.tar.bz2
  tar xjvf libvpx-1.5.0.tar.bz2
  cd libvpx-1.5.0
  PATH="$HOME/bin:$PATH" ./configure --prefix="$HOME/ffmpeg_build" --disable-examples --disable-unit-tests
  PATH="$HOME/bin:$PATH" make
  make install
  make clean
  #ffmpeg
  cd ~/ffmpeg_sources
  wget http://ffmpeg.org/releases/ffmpeg-snapshot.tar.bz2
  tar xjvf ffmpeg-snapshot.tar.bz2
  cd ffmpeg
  PATH="$HOME/bin:$PATH" PKG_CONFIG_PATH="$HOME/ffmpeg_build/lib/pkgconfig" ./configure \
  --prefix="$HOME/ffmpeg_build" \
  --pkg-config-flags="--static" \
  --extra-cflags="-I$HOME/ffmpeg_build/include" \
  --extra-ldflags="-L$HOME/ffmpeg_build/lib" \
  --bindir="$HOME/bin" \
  --enable-gpl \
  --enable-libass \
  --enable-libfdk-aac \
  --enable-libfreetype \
  --enable-libmp3lame \
  --enable-libopus \
  --enable-libtheora \
  --enable-libvorbis \
  --enable-libvpx \
  --enable-libx264 \
  --enable-libx265 \
  --enable-nonfree
  PATH="$HOME/bin:$PATH" make
  make install
  make distclean
  hash -r

.. code:: tcsh

  apt-get update
  apt-get -y install autoconf
  apt-get -y install automake
  apt-get -y install build-essential
  apt-get -y install libass-dev
  apt-get -y install libfreetype6-dev
  apt-get -y install libsdl1.2-dev
  apt-get -y install libtheora-dev
  apt-get -y install libtool
  apt-get -y install libva-dev
  apt-get -y install libvdpau-dev
  apt-get -y install libvorbis-dev
  apt-get -y install libxcb1-dev
  apt-get -y install libxcb-shm0-dev
  apt-get -y install libxcb-xfixes0-dev
  apt-get -y install pkg-config
  apt-get -y install texinfo
  apt-get -y install zlib1g-dev
  apt-get -y install yasm
  apt-get -y install libx264-dev
  apt-get -y install cmake
  apt-get -y install mercurial
  apt-get -y install libfdk-aac
  apt-get -y install libopus-dev