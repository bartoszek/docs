Let there be color
==================

http://hi.cs.waseda.ac.jp/~iizuka/projects/colorization/en/

https://github.com/satoshiiizuka/siggraph2016_colorization

install torch
.............

http://torch.ch/docs/getting-started.html

install torch dependencies (su) for each machine

.. code:: tcsh

  apt-get install curl
  curl -s https://raw.githubusercontent.com/torch/ezinstall/master/install-deps | bash

in /home for each user

.. code:: tcsh

  git clone https://github.com/satoshiiizuka/siggraph2016_colorization.git
  ./download_model.sh
  
in colorize.lua make sure to have full path for the download_model

.. code:: tcsh

  torch.load( '/home/luluf/siggraph2016_colorization/colornet.t7' )