Desktop Install 
===============

install all the apps I love to use everyday ..

Add Repositories
................

add these repositories to the system

.. code:: tcsh

   apt-add-repository --yes ppa:hugin/hugin-builds
   apt-add-repository --yes ppa:zarquon42/meshlab
   add-apt-repository --yes ppa:videolan/stable-daily
   add-apt-repository --yes ppa:otto-kesselgulasch/gimp
   add-apt-repository --yes ppa:webupd8team/java
   add-apt-repository --yes ppa:mc3man/trusty-media
   add-apt-repository --yes ppa:ubuntu-wine/ppa
   apt-get --yes update
   apt-get -y dist-upgrade

Get more stuffs ...
...................

.. image:: /images/Filelight.jpg
   
.. code:: tcsh

  apt-get install --yes gparted filelight xosview 
  apt-get install --yes hfsplus hfsprogs hfsutils 
  apt-get install --yes vlc flashplugin-installer pepperflashplugin-nonfree 
  apt-get install --yes libreoffice libreoffice-gtk libreoffice-style-sifr 
  apt-get install --yes chromium-browser firefox thunderbird transmission 
  apt-get install --yes gimp inkscape hugin meshlab 
  apt-get install --yes kdenlive filezilla winff
  
Get even more stuffs ...
........................

.. image:: /images/wine-logo.jpg
  :scale: 50 %
  
install wine to run windows apps on linux

.. code:: tcsh

  apt-get install --yes wine
  
.. image:: /images/java.jpg
  :scale: 50 %
  
install java if you need it

.. code:: tcsh
  
  apt-get install --yes oracle-java9-installer
  
Finish your stuffs
..................

.. code:: tcsh
  
  apt-get --yes update
  apt-get -y dist-upgrade
