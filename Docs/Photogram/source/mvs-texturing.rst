mvs-texturing
=============

.. image:: /images/mvs-texturing.png
  :scale: 75 %
  
Web references
..............

http://www.gris.informatik.tu-darmstadt.de/projects/mvs-texturing/

http://www.gris.informatik.tu-darmstadt.de/~miwaecht/download/Waechter-2014-Texturing.pdf

https://github.com/nmoehrle/mvs-texturing

build
.....

.. code:: tcsh

  git clone https://github.com/nmoehrle/mvs-texturing.git
  cd mvs-texturing/
  mkdir build && cd build
  cmake -DRESEARCH=ON ..
  make
  
command
.......

.. code:: tcsh

  texrecon take1_mve::undistorted take1_mve/Poisson.ply take1_mve/textured
