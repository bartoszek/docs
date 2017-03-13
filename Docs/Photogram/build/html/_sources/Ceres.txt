Build Ceres
===========

Ceres Solver is an open source C++ library for modeling and solving large, complicated optimization problems

get SuiteSparse
...............

http://faculty.cse.tamu.edu/davis/suitesparse.html

http://faculty.cse.tamu.edu/davis/SuiteSparse/SuiteSparse-4.4.6.tar.gz

add Metis to Suitesparse
..............................

http://www.math.univ-paris13.fr/~cuvelier/mainsu35.html

http://glaros.dtc.umn.edu/gkhome/fsroot/sw/metis/OLD

decompresser metis.4.0.1 dans /SuiteSparse

cd to metis-4.0 and edit the Makefile.in file.  I recommend making these changes to metis-4.0/Makefile.in

.. code:: tcsh

  CC = gcc
  OPTFLAGS = -O3
        
éditer le fichier metis-4.0/Lib/rename.h et remplacer la dernière ligne du fichier :

.. code:: tcsh

  #define log2 __log2#
  #define log2 METIS__log2#
  
utile ?

.. code:: tcsh

  apt-get install libsuitesparse-metis-*
  
build SuiteSparse
.................

edit /SuiteSparse/SuiteSparse_config/SuiteSparse_config.mk

.. code:: tcsh

  SPQR_CONFIG = -DHAVE_TBB
  TBB = -ltbb
  
.. code:: tcsh

  cd /SuiteSparse
  make library
  sudo make install
  
install Ceres
.............

http://ceres-solver.org/building.html

https://github.com/openMVG/openMVG/blob/master/src/third_party/ceres-solver/docs/source/building.rst

.. code:: tcsh

  apt-get install cmake
  apt-get install libgoogle-glog-dev
  apt-get install libatlas-base-dev
  apt-get install libeigen3-dev
  apt-get install libsuitesparse-dev
  
Install Intel's Threading Building Blocks
.........................................

.. code:: tcsh

  apt-get install libtbb-dev
  
build gflags
............

https://github.com/gflags/gflags

.. code:: tcsh

  git clone https://github.com/gflags/gflags.git
  mkdir gflags-build
  cd gflags-build
  cmake . ../gflags
  make
  make install
 
build ceres
...........

.. code:: tcsh
  
  git clone https://ceres-solver.googlesource.com/ceres-solver
  mkdir ceres_Build
  cd ceres_Build/
  cmake . ../ceres-solver/
  make -j 8
  sudo make install
  cd ..