Style-Swap
==========

.. image:: /images/styleswap.jpg
  :scale: 100 %
  
web link
........

https://github.com/rtqichen/style-swap

install
.......
  
reinstall and update torch

.. code:: tcsh

  luarocks install torch
  luarocks install nn
  luarocks install cudnn
  luarocks install cutorch
  luarocks install cunn
  luarocks install nninit
  luarocks install autograd

in ~/.bashrc

.. code:: tcsh

  export LUA_PATH="/home/render/style-swap/?.lua;$LUA_PATH"