Scanalyze
=========

.. image:: /images/scanalyze.gif

Web Reference
.............

https://github.com/nmoehrle/scanalyze

http://graphics.stanford.edu/software/scanalyze/

build scanalyze
...............

install Tcl/Tk

.. code:: tcsh

  apt-get install tcl
  apt-get install tk
  apt-get install tcl8.6-dev 
  apt-get install tk8.6-dev
  apt-get install xorg-dev
  
download sources

.. code:: tcsh

  git clone https://github.com/kyzyx/scanalyze
  cd scanalyze
  
modifier le fichier Makedefs.linux

.. code:: tcsh

  CXX = rajouter -> -DUSE_INTERP_RESULT
  INCLUDES += -I../.. \
	    -I../../auxlibs/include/tnt \
	    -I/usr/include/tcl8.6
  LIBPATHS = -L../../auxlibs/lib/Linux -L/usr/lib -L/usr/X11R6/lib -L/usr/include/tcl8.6
  
modifier le fichier togl.c

.. code:: tcsh

  #elif TK_MAJOR_VERSION==8 && TK_MINOR_VERSION==6
  #  include "/usr/include/tcl8.6/tk-private/generic/tkInt.h"

.. code:: tcsh

  make
  
run scanalyze
.............

.. code:: tcsh

  export SCANALYZE_DIR=`pwd`
  ./scanalyze.debug