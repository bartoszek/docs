Nvidia Drivers Install 
======================

.. image:: /images/nvidia.jpg

by default Kubuntu will install the "nouveau" driver which is not well suited 
for cgi applications.

Desactivating nouveau driver
............................

in /etc/default/grub , edit the following lines

::

 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rdblacklist=nouveau nouveau.modeset=0"
 GRUB_GFXMODE=1280x800
 
regenerate grub conf files and updates the existing initramfs

.. code:: tcsh

  update-grub
  update-initramfs -u
  
Installing the Nvidia drivers
.............................

reboot and switch to console mode (Ctrl-Alt-F1)

stop the display manager deamon

* Kubuntu 12.04 or 14.04

.. code:: tcsh

  service kdm stop
  
* Kubuntu 15.04

.. code:: tcsh

  service sddm stop
  
Download the driver file from Nvidia web site (I 
usually copy the driver .run file to /var/tmp) and recompile it. 

.. code:: tcsh
 
  cd /var/tmp
  chmod 777 NVIDIA-Linux-x86_64-xxx.yy.run
  ./NVIDIA-Linux-x86_64-xxx.yy.run
  
when asked , install the 32bits libraries as they are needed later for 
SoftimageXSI to run correctly.

When succesfully finished , reboot or restart the display manager.

.. code:: tcsh

  service kdm start

you can check the driver settings (in a terminal)

.. code:: tcsh

  nvidia-settings
  
Nvidia web site and downloads
.............................

which card am I using ?

.. code:: tcsh

  lspci | grep VGA
  
http://www.nvidia.com/Download/index.aspx?lang=en-us

s00X : GeForce GTX680
http://www.nvidia.com/download/driverResults.aspx/90279/en-us

.. code:: tcsh

  wget https://www.dropbox.com/s/cioabkxm7dpb3vp/NVIDIA-Linux-x86_64-352.21.run?dl=0 -O /var/tmp/NVIDIA-Linux-x86_64-352.21.run


v00X : GeForce 8800GTS
http://www.nvidia.com/download/driverResults.aspx/91217/en-us

.. code:: tcsh

  **Kubuntu 14.04**
  wget https://www.dropbox.com/s/1z0r20wgej8407n/NVIDIA-Linux-x86_64-340.76.run?dl=0 -O /var/tmp/NVIDIA-Linux-x86_64-340.76.run
  **Kubuntu 15.10**
  wget https://www.dropbox.com/s/t6rqh96ph2q7zz0/NVIDIA-Linux-x86_64-340.93.run?dl=0 -O /var/tmp/NVIDIA-Linux-x86_64-340.93.run
  
a word from linus
.................

http://www.techmansworld.com/2012/06/linus-torvalds-creator-of-linux-to.html

.. image:: /images/linus.jpg
  
  