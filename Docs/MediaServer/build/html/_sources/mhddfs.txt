mhddfs
======

Web References
..............

https://romanrm.net/mhddfs

http://svn.uvw.ru/mhddfs/trunk/README

/etc/fstab
..........

getting the uid of the device

.. code:: tcsh

  blkid /dev/sdxx
  /dev/sdd1: LABEL="GrosseMaison3" UUID="i" TYPE="ext4"

.. code:: tcsh

  vi /etc/fstab
  #disques medias
  UUID=a966ac96-19b1-4dbf-849f-1d2f5e3e06aa /mnt/media1 ext4 users,defaults 0 2
  UUID=03ac3e02-5d4f-45e2-bd11-a4f293eaf059 /mnt/media2 ext4 users,defaults 0 2
  UUID=3f17bcd6-6a02-4bf2-b636-442d77b63bb8 /mnt/mybackup ext4 users,defaults 0 2
  mhddfs#/mnt/media1,/mnt/media2 /mnt/media fuse defaults,allow_other 0 0


