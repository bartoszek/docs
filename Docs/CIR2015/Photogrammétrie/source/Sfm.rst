Structure From Motion
=====================

La reconstruction 3D à partir d'images, image-based 3D reconstruction en anglais, désigne la technique qui permet d'obtenir une représentation en trois dimensions d'un objet ou d'une scène à partir d'un ensemble d'images prises sous différents points de vue de l'objet ou de la scène.

D'une manière plus générale, le problème appelé reconstruction 3D est le suivant : on dispose d'une ou plusieurs représentations en 2D d'un objet et on souhaite déterminer les coordonnées des éléments visibles sur ces représentations dans un repère de l'espace réel 3D.

il existe plusieurs logiciels permettant de faire cette reconstruction.

**Logiciels OpenSource (libre)**
................................

  * openMVG :  http://imagine.enpc.fr/~moulonp/openMVG/
  * TheiaSfm : http://www.theia-sfm.org/
  * MVE : http://www.gcc.tu-darmstadt.de/home/proj/mve/
  * bundler : http://www.cs.cornell.edu/~snavely/bundler/
  
**Logiciels commerciaux**
.........................

  * Agisoft Photoscan : http://www.agisoft.com/
  * Capturing Reality : https://www.capturingreality.com/
  * Autodesk 123D Catch : http://www.123dapp.com/catch
  
| La première étape consiste a séparer les images pour lesquelles nous disposons des données de focales et taille du capteur et celles ou ces données sont manquantes.
| Une première passe nous permet de choisir automatiquement la paire d'images qui va permettre d'initialiser le processus incrémental de reconstruction.
| Dans une seconde passe nous introduisons alors toutes les photos collectées et la paire d'images sélectionnées précédemment.

**Étapes de reconstruction**
............................

-Extraction des points significatifs dans les images (Features).Il existe plusieurs types de descripteur pour cela (SIFT,A-KAZE).les descripteurs de type A-Kaze permettent de trouver plus de correspondances.
  
.. figure:: images/features.jpg
   :scale: 80 %
   :align: center

   exemple de features de type A-Kaze obtenues apres analyse des images
   
-Recherches des correspondances entre toutes les features pour toutes les images traitées.(fig. 5)

-Reconstruction incrémentale des paramètres extrinsèques et intrinsèques de la camera (bundler adjustment)

-Une dernière passe peut être faite pour éliminer les points non robustes (robust estimation)
  
-On obtient alors une scène 3D contenant toutes les cameras reconstruites ainsi qu'un nuage de points décrivant de façon sommaire l'objet.(fig. 6)

.. figure:: images/mysnap20.jpg
   :scale: 100 %
   :align: center
   
   exemple de scène obtenue aprés reconstruction incrémentale
   
   ici dans UMVE
   
.. figure:: images/mysnap8.jpg
   :scale: 80 %
   :align: center
   
   exemple de nuage de points obtenu aprés reconstruction incrémentale
   
   ~20000 points
   
   
