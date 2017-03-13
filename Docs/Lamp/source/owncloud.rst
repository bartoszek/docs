Install Owncloud
================

.. image:: /images/owncloud.png
  :scale: 80 %
  
additional packages
...................

.. code:: tcsh

  su -
  apt-get install apache2 mariadb-server libapache2-mod-php5
  apt-get install php5-gd php5-json php5-mysql php5-curl
  apt-get install php5-intl php5-mcrypt php5-imagick
  service apache2 restart
  
download owncloud https://download.owncloud.org/community/owncloud-8.1.3.tar.bz2

.. code:: tcsh

  tar -xjf owncloud-x.y.z.tar.bz2
  mv owncloud /var/www
  
set permissions
...............

run this script in /var/www

.. code:: tcsh

  #!/bin/bash
  ocpath='/var/www/owncloud'
  htuser='www-data'
  htgroup='www-data'
  find ${ocpath}/ -type f -print0 | xargs -0 chmod 0640
  find ${ocpath}/ -type d -print0 | xargs -0 chmod 0750
  chown -R root:${htuser} ${ocpath}/
  chown -R ${htuser}:${htgroup} ${ocpath}/apps/
  chown -R ${htuser}:${htgroup} ${ocpath}/config/
  chown -R ${htuser}:${htgroup} ${ocpath}/data/
  chown -R ${htuser}:${htgroup} ${ocpath}/themes/
  chown root:${htuser} ${ocpath}/.htaccess
  chown root:${htuser} ${ocpath}/data/.htaccess
  chmod 0644 ${ocpath}/.htaccess
  chmod 0644 ${ocpath}/data/.htaccess
  
dans /var/www/owncloud/config/config.php rajouter l'IP externe du serveur

.. code:: tcsh

 'trusted_domains' => 
  array (
    0 => 'localhost',
    1 => '82.127.216.226',
  ),
  
Uploading big files
...................

https://doc.owncloud.org/server/8.1/admin_manual/configuration_files/big_file_upload_configuration.html

edit /etc/php5/apache2/php.ini

.. code:: tcsh

  upload_max_filesize = 16G
  post_max_size = 16G
  
Memcache
........

https://owncloud.org/blog/making-owncloud-faster-through-caching/

install php5-apcu version 4.0.6 (see details in comments)

.. code:: tcsh

  cd /tmp
  wget http://mirrors.kernel.org/ubuntu/pool/universe/p/php-apcu/php5-apcu_4.0.6-1_amd64.deb
  dpkg -i php5-apcu_4.0.6-1_amd64.deb
  rm php5-apcu_4.0.6-1_amd64.deb
  service apache2 restart
  cp /usr/share/doc/php5-apcu/apc.php /var/www/html/
  
check localhost/html/apc.php5 in a browser

.. code:: tcsh

  vi /var/www/owncloud/config/config.php5

add key : 'memcache.local' => '\OC\Memcache\APCu',

.. code:: tcsh

  service apache2 restart

Performance Tuning
..................

https://doc.owncloud.org/server/8.1/admin_manual/configuration_server/performance_tuning.html

themes 
......

https://doc.owncloud.org/server/8.1/developer_manual/core/theming.html

use https
.........

https://doc.owncloud.org/server/8.1/admin_manual/configuration_server/harden_server.html

youtube user channel
....................

https://www.youtube.com/playlist?list=PLtZe22ggl2YBi1u2dH0qg9fgnym5DwYbW

use occ
.......

https://doc.owncloud.org/server/7.0/admin_manual/configuration/occ_command.html

External Storage (Dropbox)
..........................

https://doc.owncloud.org/server/8.1/admin_manual/configuration_files/external_storage_configuration_gui.html

Web References
..............

https://doc.owncloud.org/server/7.0/admin_manual/installation/source_installation.html

https://www.digitalocean.com/community/tutorials/how-to-install-owncloud-and-configure-owncloud-apps-on-an-ubuntu-12-04-vps

