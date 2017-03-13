VripPack
========

VripPack is a package for volumetrically merging a set of range images.

Web references
..............

https://graphics.stanford.edu/software/vrip/

https://graphics.stanford.edu/software/vrip/guide/

https://github.com/mattjr/structured

building
........

.. code:: tcsh

  git clone https://github.com/mattjr/structured
  cd structured/vrip/
  
to get makedepend and ld -ltk nad ld -ltcl working

.. code:: tcsh

  apt-get install xutils-dev
  ln -s /usr/lib/x86_64-linux-gnu/libtk8.6.so /usr/lib/x86_64-linux-gnu/libtk.so
  ln -s /usr/lib/x86_64-linux-gnu/libtcl8.6.so /usr/lib/x86_64-linux-gnu/libtcl.so
  
modifier le fichier vrip/src/compile-flags

.. code:: tcsh

  INCLS = -I. -I$(ROOT)/include -I/usr/include/tcl8.4  -I/usr/include/tcl -I/usr/include/tcl8.6
  LIBPATHS = -L. -L$(ROOT)/lib -L$(ROOT)/src/libply -L$(ROOT)/src/linear -L$(ROOT)/src/softrender -L/usr/include/tcl8.6
  
.. code:: tcsh

  make clobber
  make depend
  make
  
run vrip
........

.. code:: tcsh

  export VRIP_DIR=/mnt/media/Projects/Photogrametry/structured/vrip/src/vrip/
  export PATH="/mnt/media/Projects/Photogrametry/structured/vrip/bin:$PATH"
  export LD_LIBRARY_PATH="/mnt/media/Projects/Photogrametry/structured/vrip/lib/"
  vrip -noui
  vrip
  
http://graphics.stanford.edu/software/vrip/vrip_roadmap.html

lorsqu'on a le prompt faire vrip pour avoir la liste des commandes

.. code:: tcsh

   vrip_avgdown 
   vrip_avgdownrle 
   vrip_blurvb 
   vrip_calibraterotation 
   vrip_chair 
   vrip_copyright 
   vrip_cube 
   vrip_cuberle 
   vrip_cylinderrle 
   vrip_ellipse 
   vrip_ellipserle 
   vrip_extendplyedges 
   vrip_extract 
   vrip_fillplygaps 
   vrip_fillrle 
   vrip_getvoxelrle 
   vrip_gumdrop_torus 
   vrip_infonormrle 
   vrip_inforle 
   vrip_merge_time 
   vrip_newgrid 
   vrip_newgridnormrle 
   vrip_newgridrle 
   vrip_param 
   vrip_plycleanmesh 
   vrip_plycleanrangemesh 
   vrip_plyconf 
   vrip_plydmap 
   vrip_rangegridtomesh 
   vrip_rangescan 
   vrip_rangescanedgesrle 
   vrip_rangescanlin 
   vrip_rangescannormrle 
   vrip_rangescanpersp 
   vrip_rangescanrle 
   vrip_rangescanrlenotree 
   vrip_rangescantree 
   vrip_rangescanxfrle 
   vrip_readflatgrid 
   vrip_readgrid 
   vrip_readrawimages 
   vrip_render_view 
   vrip_resamp_range_time 
   vrip_sinewave 
   vrip_slicer 
   vrip_tess_time 
   vrip_testvascanner 
   vrip_transpxyrle 
   vrip_transpxz 
   vrip_transpxzrle 
   vrip_transpyz 
   vrip_transpyzrle 
   vrip_varfromconst 
   vrip_volSize 
   vrip_writeden 
   vrip_writeflatgrid 
   vrip_writegrid 
   vrip_writegridnorm