Pyramid Web Framework
=====================

.. image:: /images/pyramid-logo.jpg
  :scale: 50 %
  
installing Pyramid
..................

http://pyramid.readthedocs.org/en/latest/narr/install.html#installing-chapter

.. code:: tcsh

  su -
  easy_install virtualenv
  export VENV=~/env
  virtualenv $VENV
  $VENV/bin/easy_install "pyramid==1.5.7"
  
Glossary
========

* scaffold

A project template that generates some of the major parts of a Pyramid application and helps users to quickly get started writing larger applications. Scaffolds are usually used via the pcreate 
command.

Pyramid comes with a variety of scaffolds that you can use to generate a project. Each scaffold makes different configuration assumptions about what type of application you're trying to construct.

These scaffolds are rendered using the pcreate command that is installed as part of Pyramid.

* package

A directory on disk which contains an __init__.py file, making it recognizable to Python as a location which can be import -ed. A package exists to contain module files.

a voir:

.. code:: tcsh

  virtual envs in python
  video youtube pyramids projects

Web ressources
..............

http://pyramid.readthedocs.org/en/latest/

http://pyramid.readthedocs.org/en/latest/narr/project.html#project-narr

https://github.com/indypy/todopyramid

http://www.sqlalchemy.org/