OpenMVG
=======

.. image:: /images/openMVG_Logo.png

Web references
..............

http://imagine.enpc.fr/~moulonp/openMVG/index.html

https://github.com/openMVG/openMVG/

Docs
....

http://openmvg.readthedocs.org/en/latest/

openMVG pipeline
................

.. code:: tcsh

  python /shared/Code/openMVG-build/software/SfM/SfM_SequentialPipeline.py originales/ MVG/
  python /shared/Code/openMVG-build/software/SfM/SfM_GlobalPipeline.py originales/ MVG/
  
modifiy some parameters for best results

.. code:: tcsh

  openMVG_main_ComputeFeatures -> , "-m", "AKAZE_FLOAT" , "-p", "HIGH"] )
  openMVG_main_ComputeMatches -> , "-r" , ".8" , "-f" , "1"] )
  openMVG_main_IncrementalSfM -> , "-a" , "xxxx.jpg" , "-b" , "yyyy.jpg"] )
  
see descriptors
...............

.. code:: tcsh

  openMVG_main_exportKeypoints -i mvg/matches/sfm_data.json -d mvg/matches/ -o mvg/

Color Harmonisation
...................

openMVG_main_ColHarmonize -i with the input sfm_data.json file -m the matching file matches.X.txt with X f/e/h depending of the constraint you will choose in ComputeMatches.

.. code:: tcsh

  openMVG_main_ColHarmonize -i ./MVG/matches/sfm_data.json -m ./MVG/matches/matches.f.txt -o . -r 1

Other Tools
...........

/shared/Code/openMVG-build/Linux-x86_64-RELEASE/

.. code:: tcsh

  openMVG_main_ColHarmonize [-i|--input_file] path to a SfM_Data scene[-m|--sMatchesFile path] [-o|--outdir path] [-s|--selectionMethod int] [-r|--referenceImage int]
  openMVG_main_openMVG2CMPMVS
  openMVG_main_openMVG2MESHLAB
  openMVG_main_openMVG2MVE2
  openMVG_main_openMVG2MVSTEXTURING
  openMVG_main_openMVG2PMVS
  ui_openMVG_control_points_registration

build OpenMVG
.............

https://raw.githubusercontent.com/openMVG/openMVG/master/BUILD

.. code:: tcsh

  apt-get install libpng-dev libjpeg-dev libtiff-dev libxxf86vm1
  apt-apt-get install libxxf86vm-dev libxi-dev libxrandr-dev
  apt-get install graphviz
  apt-get install cmake
 
more
  
.. code:: tcsh

  apt-get install mesa-common-dev (instead of mesa-dev)
  apt-get install libboost-program-options-dev
  apt-get install qt4-qmake
  apt-get install qt4-dev-tools
  apt-get install libqtcore4
  apt-get install python-glpk glpk-util
  apt-get install coinor-cbc
  apt-get install coinor-clp
  apt-get install coinor-libclp-dev
  apt-get install coinor-libclp1
  apt-get install coinor-libcbc-dev
  apt-get install coinor-libcgl-dev
  apt-get install coinor-libosi-dev
  apt-get install libglpk-dev
  
.. code:: tcsh

  git clone --recursive https://github.com/openMVG/openMVG.git
  mkdir openMVG_Build
  cd openMVG_Build
  
from openMVG

.. code:: tcsh

  cmake -DCMAKE_BUILD_TYPE=RELEASE -DOpenMVG_BUILD_TESTS=ON -DOpenMVG_BUILD_EXAMPLES=ON . ../openMVG/src/
  make
  make install
  
from openMVS

.. code:: tcsh

  current_path=`pwd`
  cmake -DCMAKE_BUILD_TYPE=RELEASE . ../openMVG/src/ -DCMAKE_INSTALL_PREFIX=$current_path/openMVG_install
  make
  make install
  
how many cores ? (use make instead it fucks mddhd!)

.. code:: tcsh

  cat /proc/cpuinfo | grep processor | wc -l
  make -j nbcores
  

 