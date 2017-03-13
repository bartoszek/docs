Apache2 Server
==============

.. image:: /images/Apache.png
  
install
.......

.. code:: tcsh

  su -
  apt-get update
  apt-get install apache2

change default DocumentRoot value
.................................

.. code:: tcsh
 
  vi /etc/apache2/sites-available/000-default.conf
  change value : DocumentRoot /var/www

Activate ssl
............

Pour activer les connexions sécurisées à votre serveur Apache (https):

.. code:: tcsh

  a2enmod ssl
  a2ensite default-ssl
  service apache2 reload
 
Permissions
...........

add user maison to group www-data and set permissions to /var/www

.. code:: tcsh

  usermod -a -G www-data maison
  chgrp www-data /var/www
  chmod 775 /var/www
  chmod g+s /var/www
  
create links to Docs 
....................

(logged as user maison)

.. code:: tcsh

  ln -s /mnt/media/Docs/ /var/www/Docs
  ls -al
  lrwxrwxrwx  1 maison www-data   15 sept. 10 17:11 Docs -> /mnt/media/Docs/
  
Web links
.........

http://httpd.apache.org/docs/

https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps

https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts