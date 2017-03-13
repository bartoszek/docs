kdenlive with Kubuntu 15
========================

.. image:: /images/Kdenlive_logo.png
  
Web References
..............

https://userbase.kde.org/Kdenlive/Manual

https://community.kde.org/Kdenlive/Development/KF5

compiling vid.stab
..................

https://github.com/georgmartius/vid.stab

.. code:: tcsh

    git clone https://github.com/georgmartius/vid.stab
    cd vid.stab/
    cmake .
    make
    sudo make install

Compiling MLT with Qt5 support
..............................

.. code:: tcsh

  apt-get install build-essential pkg-config \
 libavformat-dev libavdevice-dev frei0r-plugins-dev libgtk2.0-dev libexif-dev \
 libmovit-dev libsdl1.2-dev libsox-dev libxml2-dev \
 ladspa-sdk libcairo2-dev libswscale-dev qtscript5-dev libqt5svg5-dev \ 
 libqt5opengl5-dev libepoxy-dev libeigen3-dev libfftw3-dev kdelibs5-plugins

Get the latest release from https://github.com/mltframework/mlt/releases/latest
 
.. code:: tcsh

  tar -xvf mlt-0.9.8.tar.gz
  INSTALL_PREFIX=/var/tmp
  cd /var/tmp/mlt-0.9.8
  ./configure --enable-gpl --enable-gpl3 --prefix=$INSTALL_PREFIX \
  --qt-includedir=/usr/include/x86_64-linux-gnu/qt5 --qt-libdir=/usr/lib/x86_64-linux-gnu
  make
  make install
  cd $INSTALL_PREFIX/bin
  
check that your melt is linked to QT5 /KF5 libraries using the ldd command

.. code:: tcsh

  ldd $INSTALL_PREFIX/lib/mlt/libmltqt.so
 
blacklist Qt4 filters

.. code:: tcsh

  vi $INSTALL_PREFIX/share/mlt/frei0r/blacklist.txt
  
add these lines to the file:

.. code:: tcsh

  frei0r.facebl0r
  frei0r.facedetect
  
Get the Qt5/KF5 branch of Kdenlive
..................................

.. code:: tcsh

  cd /var/tmp
  mkdir kdenlive_git
  cd kdenlive_git
  git clone git://anongit.kde.org/kdenlive.git
  cd kdenlive
  mkdir build
  cd build
  
Compile Kdenlive
................

.. code:: tcsh

  apt-get install libkf5newstuff-dev libkf5notifications-dev libkf5notifyconfig-dev libkf5plotting-dev \
  extra-cmake-modules  kdoctools-dev libsm-dev libv4l-dev libav-tools cmake qtdeclarative5-dev
  
build Kdenlive with the following options

.. code:: tcsh

  export LD_LIBRARY_PATH=$INSTALL_PREFIX/lib
  export XDG_DATA_DIRS=$INSTALL_PREFIX/share:$XDG_DATA_DIRS:/usr/share
  PKG_CONFIG_PATH=$INSTALL_PREFIX/lib/pkgconfig cmake .. -DCMAKE_INSTALL_PREFIX=$INSTALL_PREFIX
  
Problems with missing libraries
...............................

.. code:: tcsh

  locate libGL.so
  locate libEGL.so
  ln -s /usr/lib/libGL.so.340.93 /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2.0
  ln -s /usr/lib/libEGL.so.340.93 /usr/lib/x86_64-linux-gnu/mesa-egl/libEGL.so.1.0.0
  
.. code:: tcsh

  make -j4 install
  $INSTALL_PREFIX/bin/kdenlive
 
The above command should start kdenlive.

