Softimage Specifics Install 
===========================

Installing Softimage XSI on Kubuntu
...................................

.. image:: /images/xsi3.jpg
  :scale: 50 %
  
`Softimage EOL anouncement`_ or why you shouldn't buy Autodesk Software anymore.

* Softimage 2012-SP1 to 2015-SP1

Softimage was not supported on Kubuntu.Only CentOS and RedHat.You'll need some hacks to get around that.

install old libjpeg62

.. code:: tcsh

  apt-get install --yes libjpeg62
  
some symlinks and dirs

.. code:: tcsh

  ln -s /usr/lib /usr/lib64
  ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.5 /usr/lib/libtiff.so.3
  mkdir /usr/tmp
  chmod 777 /usr/tmp

* Softimage 2015-SP1

`Download Softimage 2015 SP1 for linux`_

or get it from /shared/sys/AUTODESK/

copy and extract the file to /var/tmp.then execute the setup command.you need to be root to do that.

.. code:: tcsh

  su -
  
you'll also need to redirect the display to see the installation gui
 
.. code:: tcsh

  setenv DISPLAY :0.0
  
.. image:: /images/display1.png

accepts display connection (in a user (non root) shell)

.. code:: tcsh

  xhost +
  
.. image:: /images/display2.png

launching setup
...............

in your root shell

.. code:: tcsh

  cd /var/tmp
  tar -xvzf Autodesk_Softimage_2015_SP1_English_Linux_64bit.tar.gz
  cd /var/tmp/Softimage-2015_SP1.140-linux64
  chmod 777 setup _setup
  ./setup
  
.. image:: /images/xsi1.png

follow the installation menus.choose Network licensing and type the name of your license server host,then Add.Don't bother about the last popup that tells you that the installation didn't complete 
well.

you can change the license host name in /usr/Softimage/Softimage_2015_SP1/.xsi_2015_SP1

.. code:: tcsh

  # Set the ADSKFLEX_LICENSE_FILE
  setenv ADSKFLEX_LICENSE_FILE "@myserver"

almost there !
..............

*update the libadlmint dso*

.. code:: tcsh

  cp /var/tmp/libadlmint.so.9.0.23 /usr/Softimage/Softimage_2015_SP1/Application/bin
  chmod a+rwx /usr/Softimage/Softimage_2015_SP1/Application/bin/libadlmint.so.9.0.23

To get rid of the infamous undefined symbol: `_XGetRequest`_ in Softimage 2015

.. code:: tcsh

  rm /usr/Softimage/Softimage_2015_SP1/Application/mainwin/mw/lib-amd64_linux/X11/libX11.so 
  rm /usr/Softimage/Softimage_2015_SP1/Application/mainwin/mw/lib-amd64_linux/X11/libX11.so.6
  cd /usr/Softimage/Softimage_2015_SP1/Application/mainwin/mw/lib-amd64_linux/X11
  mv libX11.so.6.3.0 libX11.so.6.3.0.bak
  ln -s /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0 libX11.so
  ln -s /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0 libX11.so.6
  ln -s /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0 libX11.so.6.3.0

copy the workgroup

the workgroup ramdisk is in /shared/etc/ramdisk.copy it first to /var/tmp then:

.. code:: tcsh

  cp -r /var/tmp/ramdisk /
  
checking registration
.....................

check and solve registrations problems : `more infos`_

.. code:: tcsh

  cd /usr/Softimage/Softimage_2015_SP1/Application/bin/
  tcsh
  source ../../.xsi_2015_SP1
  cmdreg -f XSICOMDLLs.lst
  
done !
......

launch the application

.. code:: tcsh

  /usr/Softimage/Softimage_2015_SP1/Application/bin/xsi
  
.. image:: /images/xsi2.jpg

.. _Softimage EOL anouncement: http://www.autodesk.com/products/softimage/overview
.. _Download Softimage 2015 SP1 for linux: http://download.autodesk.com/us/support/files/softimage_2015_sp1/Autodesk_Softimage_2015_SP1_English_Linux_64bit.tar.gz
.. _\_XGetRequest: http://www.si-community.com/community/viewtopic.php?f=12&t=5687&start=0
.. _more infos: http://xsisupport.com/2011/04/27/running-softimage-on-other-distros-like-ubuntu-kubuntu-pardus-and-gentoo/