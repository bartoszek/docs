Studio Specifics Install 
========================

.. image:: /images/computer.png

these are the configuration files for the studio

Backup original files
.........................

* Kubuntu 12.04

.. code:: tcsh

  cp /etc/default/grub /etc/default/grub.orig
  cp /etc/auto.master /etc/auto.master.orig
  cp /etc/init/autofs.conf /etc/init/autofs.conf.orig
  cp /etc/ldap.conf /etc/ldap.conf.orig
  cp /etc/nsswitch.conf /etc/nsswitch.conf.orig
  cp /etc/ldap/ldap.conf /etc/ldap/ldap.conf.orig
  cp /etc/pam.d/common-account /etc/pam.d/common-account.orig
  cp /etc/pam.d/common-auth /etc/pam.d/common-auth.orig
  cp /etc/pam.d/common-password /etc/pam.d/common-password.orig
  cp /etc/pam.d/common-session /etc/pam.d/common-session.orig
  cp /etc/pam.d/common-session-noninteractive /etc/pam.d/common-session-noninteractive.orig
  cp /etc/init/kdm.conf /etc/init/kdm.conf.orig

* Kubuntu 14.04 15.04

.. code:: tcsh
  
  cp /etc/default/grub /etc/default/grub.orig
  cp /etc/auto.master /etc/auto.master.orig
  cp /etc/init/autofs.conf /etc/init/autofs.conf.orig
  cp /etc/ldap.conf /etc/ldap.conf.orig
  cp /etc/init/kdm.conf /etc/init/kdm.conf.orig
  
Custom configuration files
..................................

download config files

.. code:: tcsh

  wget https://www.dropbox.com/s/9a6o7icyokg6wiu/etc.myzip?dl=0 -O /var/tmp/etc.zip
  cd /var/tmp
  unzip etc.zip
  #rm etc.zip
  
* Kubuntu 12.04

.. code:: tcsh

  cp /var/tmp/etc/default/grub /etc/default/grub
  cp /var/tmp/etc/auto.master /etc/auto.master
  cp /var/tmp/etc/auto.lamaison /etc/auto.lamaison
  chmod 644 /etc/auto.lamaison
  cp /var/tmp/etc/ldap.conf /etc/ldap.conf
  cp /var/tmp/etc/nsswitch.conf /etc/nsswitch.conf
  cp /var/tmp/etc/ldap/ldap.conf /etc/ldap/ldap.conf
  cp /var/tmp/etc/pam.d/common-account /etc/pam.d/common-account
  cp /var/tmp/etc/pam.d/common-auth /etc/pam.d/common-auth
  cp /var/tmp/etc/pam.d/common-password /etc/pam.d/common-password
  cp /var/tmp/etc/pam.d/common-session /etc/pam.d/common-session
  cp /var/tmp/etc/pam.d/common-session-noninteractive /etc/pam.d/common-session-noninteractive
  cp /var/tmp/etc/init/kdm.conf /etc/init/kdm.conf
  cp /var/tmp/etc/init/autofs.conf /etc/init/autofs.conf
  cp /var/tmp/etc/profile.d/lamaison.sh /etc/profile.d/lamaison.sh
  chmod 755 /etc/profile.d/lamaison.sh

* Kubuntu 14.04 15.04

.. code:: tcsh

  cp /var/tmp/etc/default/grub /etc/default/grub
  #blacklist nouveau
  cp /var/tmp/etc/auto.master /etc/auto.master
  #launch auto.lamaison
  cp /var/tmp/etc/auto.lamaison /etc/auto.lamaison
  #mount bluearc partitions
  chmod 644 /etc/auto.lamaison
  cp /var/tmp/etc/init/autofs.conf /etc/init/autofs.conf
  #check that autofs is launched at the right moment : 
  #start on (local-filesystems and net-device-up IFACE!=lo)
  cp /var/tmp/etc/profile.d/lamaison.sh /etc/profile.d/lamaison.sh
  #profile la maison : setenv RR_ROOT
  chmod 755 /etc/profile.d/lamaison.sh
  cp /var/tmp/etc/sssd/sssd.conf /etc/sssd/sssd.conf
  #config forr sssd - authentification ldap
  cp /var/tmp/etc/ldap.conf /etc/ldap.conf
  #config ldap