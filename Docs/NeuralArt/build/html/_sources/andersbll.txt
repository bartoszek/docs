anderbsll implementation
========================

.. image:: /images/lemmy_moebius.jpg
  :scale: 50 %
  
web link
........

https://github.com/andersbll/neural_artistic_style

https://www.reddit.com/r/MachineLearning/comments/3jhe26/artistic_style_network_in_python_yet_another/

install python stuffs
.....................

.. code:: tcsh

  apt-get install python-dev
  apt-get install python-pip
  pip install pgen
  pip install cython
  pip install scipy

install CUDArray
................

https://github.com/andersbll/cudarray

.. code:: tcsh

  git clone https://github.com/andersbll/cudarray.git
  cd cudarray/
  make
  make install
  python setup.py install
  

  
install deeppy
..............

https://github.com/andersbll/deeppy

http://andersbll.github.io/deeppy-website/installation-guide.html

.. code:: tcsh

  git clone https://github.com/andersbll/deeppy.git
  cd deeppy
  python setup.py install
  
install neural_artistic_style
.............................

.. code:: tcsh

  git clone https://github.com/andersbll/neural_artistic_style.git

download neural network
.......................

http://www.vlfeat.org/matconvnet/pretrained/

http://www.vlfeat.org/matconvnet/models/**imagenet-vgg-verydeep-19.mat**

.. image:: /images/derrico1_lulu.jpg
  :scale: 50 %