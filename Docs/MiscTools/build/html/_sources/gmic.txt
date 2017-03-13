G'MIC
=====

.. image:: /images/gmicky.jpg

http://gmic.eu/tutorial/basics.shtml

http://opensource.graphics/

http://gmic.eu/reference.shtml

https://issuu.com/dtschump/docs/gmic_slides

https://www.youtube.com/channel/UC05Y8hpbFOSQ4ivh01R_1AQ

http://blog.patdavid.net/2011/12/getting-around-in-gimp-skin-retouching.html

https://discuss.pixls.us/t/panography-patching-the-zenith-and-nadir/585

https://discuss.pixls.us/

gmic on github
..............

https://github.com/dtschump/gmic

.. code:: tcsh

  su -
  apt-get install libcurl4-gnutls-dev
  apt-get install libfftw3-dev
  apt-get install libgimp2.0-dev

.. code:: tcsh

  cd ~
  git clone https://github.com/dtschump/gmic.git
  git clone https://github.com/dtschump/gmic-community.git
  cd gmic/src
  make

Install new version
...................

https://github.com/dtschump/gmic/releases

download new version in home directory (v177 par exemple)

.. code:: tcsh

  cd ~/gmic-v.177/src
  make all
  cp gmic_gimp ~/.gimp-2.8/plug-ins/
  ./gmic -update
  
Darktable
.........

http://www.darktable.org/install/#ubuntu