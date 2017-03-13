DNS-DHCP 
========

.. image:: /images/dns-dhcp.png

Domain Name System - DNS
........................

The DNS is hosted on the virtual machine **"vmsys1"**

.. code:: tcsh

  ssh root@vmsys1
  cd /etc/bind
 
db.lamaison
...........
 
Machines and the IP they are registered on

db.192.168.32.1
...............

IP adresses and the machines they are linked to

**Any modifications have to be done in both files**

restart bind service
....................

.. code:: tcsh

  etc/init.d/bind9 restart

*The other files are backups of previous working configurations, the date of the backup is at the end of the name of each files.For example, a configuration file modified the 26th of January in 2013 
would be called "db.lamaison.13(year)01(month)26(day)"
==> db.lamaison130126 . Always make a backup before making any modifications to these files.*

Dynamic Host Configuration Protocol - DHCP
..........................................

The DHCP is hosted on the same virtual machine as the DNS

.. code:: tcsh

  ssh root@vmsys1
  vi /etc/dhcp3/dhcpd.master
  
restart dhcp service
....................

For any modification to be taken into account, you have to restart the system

.. code:: tcsh

  etc/init.d/dhcp3-server restart
 
*Same as for the DNS, other files are backups named after the date of the backups.
Always do a backup before making any modification.*