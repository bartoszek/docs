Theia  Vision Library
=====================

.. image:: /images/theia.png

Web references
..............

http://www.theia-sfm.org/index.html

https://github.com/sweeneychris/TheiaSfM

building gflags
...............



building Theia
..............

.. code:: tcsh

  apt-get install libgflags2 libgflags-dev
  apt-get install freeglut3 freeglut3-dev
  apt-get install libxmu-dev libxi-dev
  
.. code:: tcsh

  git clone https://github.com/sweeneychris/TheiaSfM.git
  cd TheiaSfM/
  mkdir theia-build
  cd theia-build
  cmake ..
  make -j4