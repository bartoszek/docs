Sphinx Documentation Generator
==============================

.. image:: /images/sphinx-logo.png
  :scale: 50 %
  
Web References
..............

http://deusyss.developpez.com/tutoriels/Python/SphinxDoc/

install sphinx
..............

http://sphinx-doc.org/install.html

.. code:: tcsh

  apt-get install python-sphinx
  
start new documentation
.......................

.. code:: tcsh

  mkdir /mnt/media/Docs/mydoc
  cd /mnt/media/Docs/mydoc
  sphinx-quickstart
  
separate source and build : yes

compile new Docs
................

.. code:: tcsh

  make html
  
read the doc theme
..................

.. code:: tcsh

  apt-get install python-pip
  pip install sphinx_rtd_theme
  
update source/conf.py
.....................

In your conf.py file:

.. code:: tcsh

  import sphinx_rtd_theme
  html_theme = "sphinx_rtd_theme"
  html_theme_path = [sphinx_rtd_theme.get_html_theme_path()]

