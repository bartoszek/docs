Multi-View Stereo
=================

Cette étape correspond a la densification des données calculées précédemment. En exploitant les correspondances entre chaque image on va reconstituer un nuage de points beaucoup plus dense (plusieurs millions de points).Ces données sont stockées dans des maps de profondeur (depth map) puis recombinées dans un seul nuage de points. Enfin un maillage polygonal est généré a partir des points.

il existe plusieurs logiciels permettant de faire cette densification.

**Logiciels OpenSource (libre)**
................................

  * openMVS :  http://cdcseacave.github.io/openMVS/
  * MVE/fssrecon : http://www.gcc.tu-darmstadt.de/media/gcc/papers/Goesele-2007-MVS.pdf
  * CMVS/PMVS : http://www.di.ens.fr/pmvs/
  
**Logiciels commerciaux**
.........................

  * Agisoft Photoscan : http://www.agisoft.com/
  * Capturing Reality : https://www.capturingreality.com/
  * Autodesk 123D Catch : http://www.123dapp.com/catch
  
**Étapes de reconstruction**
............................

.. figure:: images/mve3.jpg
   :scale: 100 %
   :align: center
   
   depth map obtenue pour une image
   
   les points sont encore organisés en grille de pixels
   
Calcul des maps de profondeur (depth map).Le logiciel estime aussi une notion de qualité des points (confidence) ainsi que le gradient de profondeur dz indiquant des fortes variations de profondeur.(fig. 9)

.. figure:: images/mve2.jpg
   :scale: 100 %
   :align: center
   
   visualisation d'une depth map (Umve)
   
   a) image originale b) dz 
   c) depth 	      e) confidence
   
Génération du nuage de points dense.(fig. 10 fig. 11)
  
.. figure:: images/mysnap12.jpg
   :scale: 80 %
   :align: center
   
   dense point cloud
   
   plusieurs millions de points
   
.. figure:: images/mysnap18.jpg
   :scale: 80 %
   :align: center
   
   dense point cloud
   
   plusieurs millions de points
   
Les points obtenus sont regroupes dans une structure de voxels (octree) puis filtrées et maillées pour générer un premier maillage polygonal,
ce maillage polygonal est alors raffiné avec divers algorithmes.(fig. 12)

.. figure:: images/mysnap19.jpg
   :scale: 80 %
   :align: center
   
   exemple de maillage polygonal
   
   la couleur est appliquée uniquement aux points
   
Application de la texture.Une texture unique est générée en choisissant la meilleure vue dans toutes les photos et assemblée par une méthode de graph-cut au niveau des paramètres uv (atlas).(fig. 13)

.. figure:: images/mysnap17.jpg
   :scale: 80 %
   :align: center
   
   le meme maillage avec sa texture appliquée
   
Cette texture exploite le maximum de résolution fournie.Elle est par contre inexploitable dans un logiciel de retouche d'images (Photoshop ou Gimp).(fig. 14)

.. figure:: images/mysnap50.jpg
   :scale: 80 %
   :align: center
   
   exemple de texture (png) obtenue aprés projection
   