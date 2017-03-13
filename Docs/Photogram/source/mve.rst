MVE
===

Web references
..............

http://www.gris.informatik.tu-darmstadt.de/projects/multiview-environment/

https://github.com/simonfuhrmann/mve

https://github.com/simonfuhrmann/mve/wiki

http://www.gris.informatik.tu-darmstadt.de/projects/floating-scale-surface-recon/

**using mve**
.............

https://github.com/simonfuhrmann/mve/wiki/MVE-Users-Guide

typical pipeline
................

.. code:: tcsh

  /mnt/media/Projects/Photogrametry/mve/apps/makescene/makescene -i originales/ mve/
  /mnt/media/Projects/Photogrametry/mve/apps/sfmrecon/sfmrecon mve
  /mnt/media/Projects/Photogrametry/mve/apps/dmrecon/dmrecon -s2 mve
  /mnt/media/Projects/Photogrametry/mve/apps/scene2pset/scene2pset -F2 mve mve/pset-L2.ply
  /mnt/media/Projects/Photogrametry/mve/apps/fssrecon/fssrecon mve/pset-L2.ply mve/surface-L2.ply
  /mnt/media/Projects/Photogrametry/mve/apps/meshclean/meshclean -t10 mve/surface-L2.ply mve/surface-L2-clean.ply
  
makescene
.........

creates a mve project in mve dir.makescene can also create a project from a bundler file.

(see Lulu's pipeline Reconstruct_MVE.pl)

.. code:: tcsh

  makescene -i originales/ mve/

sfmrecon
........

command line application that runs the SfM reconstruction on the input images

.. code:: tcsh

  sfmrecon mve/
  sfmrecon --initial-pair=0,1 mve/
  sfmrecon --max-pixels=7000000 mve/

sfmrecon reuses data in prebundle.sfm and meta.ini.(il vaut mieux effacer le projet et le regenerer pour reinitialiser les donnees.)
you can specify initial pairs with --initial-pair=0,1 for example, --max-pixels=7000000 force to use full frames

use umve to see the results

get sfm from openMVG
....................

.. code:: tcsh

  openMVG_main_openMVG2MVE2 -i mvg/reconstruction_sequential/sfm_data.json -o .
  openMVG_main_openMVG2MVE2 -i mvg/reconstruction_sequential/robust.json -o .

dmrecon
.......

runs Multi-View Stereo (MVS) to reconstruct a depth map for every input image

.. code:: tcsh

  dmrecon -s2 mve/
  dmrecon -s0 mve/
  dmrecon -f7 -s0 --force mve/
  dmrecon -s1 --keep-dz --keep-conf -p MVE/
  
-f7 option increase patch size , slower but more points.(certain values generates core dumped)
--force force reconstruction of depth maps.

use umve to see the results

scene2pset
..........

create an extremely dense point cloud as the union of all samples from all depth maps.

.. code:: tcsh

  scene2pset -n -p -c -s  -F2 MVE/ MVE/pset-L2.ply
  scene2pset -F0 mve/ mve/pset-L0.ply
  scene2pset -p -F0 mve/ mve/pset-L0.ply
  scene2pset -ddepth-L0 -iundistorted -mmask -n -s -c -p mve/ mve/pset-L0.ply
  
-p, --poisson-normals Scale normals according to confidence

masks should be one channel png (no alpha) called mask.png and saved in the views

PoissonRecon
............

from the generated point set you can use PoissonRecon directly

.. code:: tcsh

  PoissonRecon --in MVE/pset-L2.ply --out MVE/Poisson-L2.ply --verbose --color 16 --depth 10 --density
  PoissonRecon --in MVE/pset-L0.ply --out MVE/Poisson-L0.ply --verbose 
  PoissonRecon --in MVE/pset-L0.ply --out MVE/Poisson-L0.ply --verbose --color 16 --depth 8
  PoissonRecon --in MVE/pset-L0.ply --out MVE/Poisson-L0.ply --verbose --color 16 --depth 8 --density
  PoissonRecon --in MVE/pset-L0.ply --out MVE/Poisson-L0-node5.ply --verbose --color 16 --depth 8 --density --samplesPerNode 5
  PoissonRecon --in MVE/pset-L0.ply --out MVE/Poisson-L0-node20.ply --verbose --color 16 --depth 8 --density --samplesPerNode 20
  
using the --density flag to indicate that density estimates should be output with the vertices of the mesh

samplesPerNode : This floating point value specifies the minimum number of sample points that should fall within an octree node as the octree construction is adapted to sampling density. For noise-free samples, small values in the range [1.0 - 5.0] can be used. For more noisy samples, larger values in the range [15.0 - 20.0] may be needed to provide a smoother, noise-reduced, reconstruction.
    

SurfaceTrimmer
..............

.. code:: tcsh

  SurfaceTrimmer --in Poisson-L0.ply --out Poissontrim-L0.ply --trim 7
  
to remove all subsets of the surface where the sampling density corresponds to a depth smaller than 7.

fssrecon
........

Samples the implicit function defined by the input samples and produces a
surface mesh. The input samples must have normals and the "values" PLY
attribute (the scale of the samples). Both confidence values and vertex
colors are optional. The final surface should be cleaned (sliver triangles,
isolated components, low-confidence vertices) afterwards.

.. code:: tcsh

  fssrecon MVE/pset-L1.ply MVE/surface-L1.ply
  
texrecon
........

Textures a mesh given images in form of a 3D scene

.. code:: tcsh

  texrecon mve::undistorted mve/Poissontrim-L0.ply mve/textured

**building mve**
................

.. code:: tcsh

  git clone https://github.com/simonfuhrmann/mve.git
  cd mve
  make -j8

build umve
..........

install qt5
...........

.. code:: tcsh

  apt-get install qt5-default qttools5-dev-tools

.. code:: tcsh

  cd apps/umve/
  qmake 

force c++11 standart in c++

in /umve/Makefile add **-std=c++11**

.. code:: tcsh

  CXXFLAGS      = -m64 -pipe -fPIC -fopenmp -O2 -D_REENTRANT -Wall -W $(DEFINES) -std=c++11
  
.. code:: tcsh

  make -j8
  ./umve