Installation
============

Kubuntu 14.04
.............

.. code:: tcsh

  apt-get install imagemagick perlmagick

desinstallation
...............

.. code:: tcsh

  apt-get remove --purge imagemagick perlmagick imagemagick-common

Compilation
...........

http://www.imagemagick.org/script/install-source.php

http://www.imagemagick.org/script/perl-magick.php

download http://www.imagemagick.org/download/ImageMagick.tar.gz

.. code:: tcsh

  tar xvzf ImageMagick.tar.gz
  cd ImageMagick-7.0.2-9/
  ./configure -with-perl
  make
  sudo make install
  ldconfig /usr/local/lib
  
problem with perl (ld cannot find -lperl)
.........................................

.. code:: tcsh

  ln -s /usr/lib64/libperl.so.5.18 /usr/lib64/libperl.so