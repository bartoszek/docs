Recolorisation
==============

.. image:: /images/recolor.png
  :scale: 50
  
http://hi.cs.waseda.ac.jp/~iizuka/projects/colorization/en/

https://github.com/satoshiiizuka/siggraph2016_colorization

http://torch.ch/docs/getting-started.html

http://www.cs.huji.ac.il/~yweiss/Colorization/index.html

http://colorizr.io/

AutoColorize
............

http://people.cs.uchicago.edu/~larsson/colorization/

install autocolorize on renderfarm
..................................

english sources.list

.. code:: tcsh

  #------------------------------------------------------------------------------#
  #                            OFFICIAL UBUNTU REPOS                             #
  #------------------------------------------------------------------------------#
  ###### Ubuntu Main Repos
  deb http://en.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse 
  deb-src http://en.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse 
  ###### Ubuntu Update Repos
  deb http://en.archive.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse 
  deb http://en.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse 
  deb-src http://en.archive.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse 
  deb-src http://en.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse 

.. code:: tcsh

  cp sources.list /etc/apt/sources.list
  apt-get clean
  apt-get update
  apt-get --yes upgrade
  apt-get --yes autoremove
  apt-get install --yes libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler
  apt-get install --yes libatlas-base-dev
  apt-get install --yes --no-install-recommends libboost-all-dev
  apt-get install --yes libgflags-dev libgoogle-glog-dev liblmdb-dev
  apt-get install --yes python-matplotlib
  apt-get install --yes python-numpy python-scipy python-skimage
  apt-get install --yes python-pip
  pip install protobuf
  pip install autocolorize

Colorful Image Colorization
...........................

http://richzhang.github.io/colorization/

https://github.com/richzhang/colorization

Install Caffe (Kubuntu 16.04)
.............................

http://caffe.berkeleyvision.org/install_apt.html

https://github.com/BVLC/caffe/wiki/Ubuntu-16.04-or-15.10-Installation-Guide

.. code:: tcsh

    apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler
    apt-get install --no-install-recommends libboost-all-dev
    apt-get install libatlas-base-dev
    apt-get install python-dev
    apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev

.. code:: tcsh

    git clone https://github.com/BVLC/caffe.git
    cp Makefile.config.example Makefile.config
    # Adjust Makefile.config (For CPU-only Caffe, uncomment CPU_ONLY := 1 in Makefile.config)
    make all (see problem with hdf5.h)
    make test
    make runtest
    make pycaffe
    
problem with hdf5.h
...................

https://github.com/BVLC/caffe/issues/2347

python :
........

.. code:: tcsh

    apt-get install python-matplotlib
    apt-get install python-numpy python-scipy
    apt-get install python-skimage