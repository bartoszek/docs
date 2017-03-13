dmfusion
========

.. image:: /images/dmfusion.png

http://www.gris.informatik.tu-darmstadt.de/projects/multiscale-depthmap-fusion/

build
.....

wget http://www.gris.informatik.tu-darmstadt.de/projects/multiscale-depthmap-fusion/data/dmfusion-20140505.tar.gz

copier le dossier dans mve/apps

.. code:: tcsh

  cd mve/apps/dmfusion
  make -C dmfusion

construction
............

Running the software involves first building an octree using the dmfoctree app, extracting a tetrahedral mesh from the octree using dmfextract and triangulating the tetrahedral mesh using dmfsurface.

.. code:: tcsh

  dmfoctree -d depth-L2 -i undist-L2 take1_mve/ take1_mve/tmp.octree
  dmfextract -f10 take1_mve/tmp.octree take1_mve/tmp.ply
  
la tetrahedralization se bloque dans dmfextract.rendant dmfsurface inutilisable.l'option -fxx permet de trianguler l'octree au niveau donne.

ces programmes semblent obsoletes ou inacheves.