JcJohnson implementation
========================

.. image:: /images/deepart2.jpg
  :scale: 60 %
  
web link
........

https://github.com/jcjohnson/neural-style

install
.......

https://github.com/jcjohnson/neural-style/blob/master/INSTALL.md

.. image:: /images/chocolatlou.jpg
  :scale: 60 %
  
.. code:: tcsh

  su -
  apt-get install curl
  curl -s https://raw.githubusercontent.com/torch/ezinstall/master/install-deps | bash
  exit
  git clone https://github.com/torch/distro.git ~/torch --recursive
  cd ~/torch; ./install.sh
  source ~/.bashrc
  
To check that your torch installation is working, run the command th to enter the interactive shell. To quit just type exit.

.. code:: tcsh

  su -
  apt-get install libprotobuf-dev protobuf-compiler
  exit
  luarocks install loadcaffe
  cd ~/
  git clone https://github.com/jcjohnson/neural-style.git
  cd neural-style
  sh models/download_models.sh