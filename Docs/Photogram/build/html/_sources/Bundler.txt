Bundler
=======

.. image:: /images/Colosseum.jpg

Web references
..............

http://www.cs.cornell.edu/~snavely/bundler/

http://www.cs.cornell.edu/projects/bigsfm/

https://github.com/snavely/bundler_sfm

Install Bundler
...............

Download Sift ...

http://www.cs.ubc.ca/~lowe/keypoints/siftDemoV4.zip

.. code:: tcsh

  apt-get install imagemagick php5-imagick
  apt-get install gfortran
  
.. code:: tcsh

  git clone https://github.com/snavely/bundler_sfm
  cp siftDemoV4/sift bundler_sfm/bin
  cd bundler_sfm
 
edit the file src/Makefile and uncomment the line USE_CERES=true

.. code:: tcsh

  make
  