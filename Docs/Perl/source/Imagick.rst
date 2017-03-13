Imagemagick
===========

.. image:: /images/wizard.jpg
  :scale: 50 %
  
Web references
..............

http://www.imagemagick.org

http://www.imagemagick.org/download/

Install ImageMagick and perl module
...................................

.. code:: tcsh

  su -
  apt-get install libperl-dev autoconf
  
.. code:: tcsh 

  cd /var/tmp
  wget http://www.imagemagick.org/download/ImageMagick-6.9.3-8.tar.gz
  tar xvfz ImageMagick-6.9.3-8.tar.gz
  cd ImageMagick-6.9.3-8/
  ./configure --with-perl
  make
  make install
  
Color Management in PerlMagick
..............................

Color management has changed significantly between ImageMagick version 6.7.5-5 and 6.8.0-3 in order to better conform to color and grayscale standards.

The first major change was to swap -colorspace RGB and -colorspace sRGB. In earlier versions, RGB really meant non-linear sRGB. With the completion of the changes, RGB now means linear color and sRGB means non-linear color in terms of their respective colorspaces.

http://www.imagemagick.org/script/color-management.php