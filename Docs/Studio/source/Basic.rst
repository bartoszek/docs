Basic Kubuntu Install 
=====================

.. image:: /images/kubuntu-1404.jpg

Once the initial installation from .iso is finished:

super-user
..........

I like to work as a super user when installing instead of sudo ...

.. code:: tcsh

  sudo passwd
  
update and upgrade the installation:

.. code:: tcsh

  apt-get update && apt-get -y dist-upgrade
  
you will need gcc and make to install Nvidia drivers:

.. code:: tcsh

  apt-get install --yes gcc make
  
ssh and misc sh interpreters
  
.. code:: tcsh

  apt-get install --yes ssh openssh-server openssh-client csh tcsh 
  
if you want to have ssh root login available (only for LAN)

.. code:: tcsh

  vi /etc/ssh/sshd_config
  change setting to  : PermitRootLogin yes
  
autofs to mount volumes later
  
.. code:: tcsh

  apt-get install --yes autofs 
  
ldap authentification
.....................

- **Kubuntu 12.04**

12.04 works fine with nscd

.. code:: tcsh

  apt-get install --yes libpam-ldap libnss-ldap nscd
  
- **Kubuntu 14.04 LTS**

14.04 works better with sssd (nscd causes problems with mounting 
external drives and sound and burning CD's)

.. code:: tcsh

  apt-get install --yes sssd libpam-sss libnss-sss libnss-ldap
  
use kdm instead lightdm (so you don't have all user listed in the connection 
screen) . select kdm as default

.. code:: tcsh

  apt-get install --yes kdm

- **Kubuntu 15.04 - 15.10**

15.04 works better with sssd (nscd causes problems with mounting 
external drives and sound and burning CD's)

.. code:: tcsh

  apt-get install --yes sssd libpam-sss libnss-sss libnss-ldap
  
15.04 doesn't support kdm but uses sddm.To be able to log in with a unique user 
you can install the elarun theme:

.. code:: tcsh

  apt-get install sddm-theme-elarun
  
vi /usr/share/sddm/themes/elarun/Main.qlm and change the definition to 1920*1200
than select the elarun theme in the start/shutdown configuration settings.

to start the elarun theme with a french keyboard by default

.. code:: tcsh

  echo 'setxkbmap "fr"' >> /usr/share/sddm/scripts/Xsetup
  
http://www.linuxfromscratch.org/blfs/view/svn/x/sddm.html

settings for ldap authentification
..................................
::

  ldapi : 192.168.32.1
  dc=mystudio  
  3 / no / no  

bug : ldap user with automounted nfs homedir cannot login:

https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/870874

RoyalRender specifics
.....................
(this is for royalrender v 6.02.51)
http://www.royalrender.de/index.htm

.. code:: tcsh

  apt-get install --yes ibus
  
to avoid error popups in royalrender
  
.. code:: tcsh

  chmod u+s /sbin/reboot
  
all users can now poweroff and reboot (not root only)

.. code:: tcsh

  apt-get install ethtool
  ethtool -s eth0 wol g

activate Wake on Lan (WOL) on eth0.

::

    vi /etc/rc.local and add this line at the end to be sure 
    that wol is always active.
    
   # By default this script does nothing.
   ethtool -s eth0 wol g
   exit 0

more on wake on lan (in french):

http://doc.ubuntu-fr.org/wakeonlan

Misc packages
.............
  
.. code:: tcsh

  apt-get install --yes ubuntu-restricted-extras 
  apt-get install --yes gstreamer0.10-plugins-ugly libavcodec-extra-54 
  apt-get install --yes libvdpau-va-gl1 libmad0 mpg321 gstreamer1.0-libav
  apt-get install --yes unace rar unrar p7zip-rar p7zip sharutils uudeview 
  apt-get install --yes mpack arj cabextract lzip lunzip
  apt-get --yes update
  apt-get --yes upgrade 
  
Custom configuration files
..........................

download config files

.. code:: tcsh

  wget https://www.dropbox.com/s/9a6o7icyokg6wiu/etc.myzip?dl=0 -O /var/tmp/etc.zip
  wget https://www.dropbox.com/s/kderr8diwywsdum/foundry.myzip?dl=0 -O /var/tmp/foundry.zip
  cd /var/tmp
  unzip etc.zip
  unzip foundry.zip
  #rm etc.zip foundry.zip
 
Nuke
....

.. code:: tcsh

  cp -r /var/tmp/foundry/ /usr/local
  chmod -R 755 /usr/local/foundry

*Basic* : all in one command
..............................

.. code:: tcsh

  apt-get --yes update
  apt-get --yes upgrade
  apt-get install --yes gcc make autofs
  apt-get install --yes ssh openssh-server openssh-client csh tcsh
  apt-get install --yes sssd libpam-sss libnss-sss libnss-ldap
  apt-get install --yes kdm ibus ethtool
  apt-get install --yes ubuntu-restricted-extras 
  apt-get install --yes gstreamer0.10-plugins-ugly libavcodec-extra-54 
  apt-get install --yes libvdpau-va-gl1 libmad0 mpg321 gstreamer1.0-libav
  apt-get install --yes unace rar unrar p7zip-rar p7zip sharutils uudeview 
  apt-get install --yes mpack arj cabextract lzip lunzip
  chmod u+s /sbin/reboot
  apt-get --yes update
  apt-get --yes upgrade
  
.. image:: /images/plasma5.jpg