Houdini
=======

.. image:: /images/Houdini.jpg
  :scale: 30 %

Web References
..............

http://www.sidefx.com/index.php?option=com_content&task=view&id=1207&Itemid=273

linux install
.............

.. code:: tcsh

  tar -xvzf houdini-xx.y.zzz.zz-linux_x86_64_gcc4.8.tar.gz
  cd houdini-xx.y.zzz.zz-linux_x86_64_gcc4.8
  ./houdini.install
  
start and stop server
.....................

.. code:: tcsh

  /etc/init.d/sesinetd stop
  /etc/init.d/sesinetd start
  
server binary located in in /usr/lib/sesi

modify env
..........

.. code:: tcsh

  vi /opt/hfsxx.y.zzz.zz/houdini_setup_bash
  add : export LC_ALL=C
  
launch houdini
..............

.. code:: tcsh

  cd /opt/hfs15.0.244.16
  source houdini_setup
  houdini
  
Install houdini on shared
.........................

.. code:: tcsh

  cp houdini-xx.y.zzz.zz-linux_x86_64_gcc4.8.tar.gz /shared/apps/houdini/Downloads
  cd /shared/apps/houdini/Downloads
  tar -xvzf houdini-xx.y.zzz.zz-linux_x86_64_gcc4.8.tar.gz
  cd houdini-xx.y.zzz.zz-linux_x86_64_gcc4.8
  ./houdini.install

destination install folder : /shared/apps/houdini/hfsxx.y.zzz.zz

.. code:: tcsh

  vi /shared/apps/houdini/hfsxx.y.zzz.zz/houdini_setup_bash
  add : export LC_ALL=C
  
add the new version in PATH

.. code:: tcsh

  cd /shared/bin
  ln -s _houdini_version.sh houdini-xx.y.zzz
  ln -s _houdini_version.sh hython-xx.y.zzz
  
add hsite for new version

.. code:: tcsh

  cd /shared/apps/houdini/hsite
  cp -r houdini14.0 houdini15.0
  chown -R someone:users houdini15.0

the SubmitRoyalRender menu should appear under Render in the UI

New menu are defined in /shared/apps/houdini/hsite/houdini15.0/MainMenuCommon.xml

RR launch script is in /shared/apps/houdini/hsite/houdini15.0/scripts/menu/lmSubmitToRoyalRender.py

Royal Render 
............

create a file in shared/apps/royal-render/render_apps/_config like 3D08__Houdini_15_244.cfg

in shared/apps/royal-render/sub/cfg_global , add the new renderer lines to each nodes

.. code:: tcsh

  renderapp05\Name=Houdini_-15_-0_-244_-_-64
  renderapp05\Executable=/shared/apps/houdini/hfs15.0.244.16/bin/hython


