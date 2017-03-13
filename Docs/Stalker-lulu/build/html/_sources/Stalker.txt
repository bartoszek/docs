Stalker
=======

get code
........

.. code:: tcsh

  git clone https://github.com/eoyilmaz/stalker.git
  
create virtual env
..................

.. code:: tcsh

  export VENV=/mnt/media/Stalker/env
  virtualenv $VENV
  source $VENV/bin/activate
  
install python libs
...................

.. code:: tcsh

  $VENV/bin/pip install sqlalchemy
  $VENV/bin/pip install jinja2
  $VENV/bin/python setup.py develop
  
install TaskJuggler
...................

.. code:: tcsh

  gem install taskjuggler

configuring Stalker
...................

To configure Stalker and make it fit to your Studios need you should use the config.py file

.. code:: python

  export STALKER_PATH=/mnt/media/Stalker
  
create a config.py file in /mnt/media/Stalker with these config variables

.. code:: python
  
  database_engine_settings={
      "sqlalchemy.url": "sqlite:////mnt/media/Stalker/db/test1.db",
      "sqlalchemy.echo": False,
  }
  server_side_storage_path='/mnt/media/Stalker/Storage'
  admin_password='81ackK3y5'
  admin_email='sys@alamaison.fr'
  
Web references
..............

* Stalker

https://github.com/eoyilmaz/stalker


  
* Stalker 0.2.13.2 documentation

http://pythonhosted.org/stalker/

* Stalker pyramid

https://code.google.com/p/stalker-pyramid/source/checkout

.. code:: tcsh

  hg clone https://code.google.com/p/stalker-pyramid/
  
https://pypi.python.org/pypi/stalker_pyramid/0.1.0.b1
 
.. code:: tcsh

  hg clone https://stalker-pyramid.googlecode.com/hg/ stalker_pyramid

* blog

http://eoyilmaz.blogspot.fr/
  
* oyProjectManager

https://pypi.python.org/pypi/oyProjectManager

* TaskJuggler

http://www.taskjuggler.org/index.php