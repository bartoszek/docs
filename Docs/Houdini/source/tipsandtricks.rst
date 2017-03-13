Houdini Tips'n'tricks
=====================

automatic rendered images name
..............................

.. image:: /images/snap1.jpg
  :scale: 100 %
  
.. code:: tcsh

  `$HIP`/images/`strreplace("$HIPNAME",".hip","")`..exr
  
timewarp of camera motion
.........................

.. image:: /images/snap6.jpg
  :scale: 100 %
  
.. image:: /images/snap7.jpg
  :scale: 100 %
  
replace with warp node and set export (brown icon) on both nodes

.. image:: /images/snap2.jpg
  :scale: 100 %
  
timewarp value in channel node

.. image:: /images/snap3.jpg
  :scale: 100 %
  
clip node import camera transform values

.. image:: /images/snap4.jpg
  :scale: 100 %