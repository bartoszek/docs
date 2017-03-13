Blind Consistency
=================

https://github.com/nbonneel/blindconsistency

http://liris.cnrs.fr/%7Enbonneel/consistency/temporalconsistency.pdf

http://liris.cnrs.fr/%7Enbonneel/consistency/

https://www.youtube.com/watch?v=reiT2SJh96U&feature=youtu.be

Install Wine
============

https://wiki.winehq.org/Winetricks

Ubuntu 16.04
............

https://wiki.winehq.org/Ubuntu

.. code:: tcsh

  sudo add-apt-repository ppa:wine/wine-builds
  sudo apt-get update
  sudo apt-get install --install-recommends winehq-devel
  winetricks
  
Ubuntu 14.04
............

.. code:: tcsh

  apt-get install -yes wine1.6
  rm -r ~/.wine (reinit la partition windows)
  cd .wine/drive_c
  wget  https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks (get latest winetricks script)
  chmod +x winetricks 
  ./winetricks
  
.. code:: tcsh

  >Select the default wineprefix
  >Install a Windows DLL or component
  >install vcrun2013 Visual C++ 2013 libraries (fournit msvcp120,msvcr120,vcomp120)
  
.. code:: tcsh

  cd drive_c/
  git clone https://github.com/nbonneel/blindconsistency.git
  cd blindconsistency/x64/Release/
  DISPLAY= wine stabilize.exe old_man.mp4 old_man_autocolors.avi 1.0 old_man_regularized.mp4 10000 (no display)