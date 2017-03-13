Cuda
====

.. image:: /images/lineup-full.jpg
  :scale: 100 %
  
http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/#axzz40tPF5jJ8

https://developer.nvidia.com/cuda-downloads

https://developer.nvidia.com/cudnn

.. image:: /images/zappa.jpg
  :scale: 100 %
  
uninstall cuda
..............

.. code:: tcsh

  apt-get --purge remove nvidia-* cuda*

install cuda
............

.. code:: tcsh

  dpkg -i cuda-repo-<distro>_<version>_<architecture>.deb
  apt-get update
  apt-get install cuda
  
create a local repo in /var

install cuda and associated nvidia driver

install cudnn
.............

.. code:: tcsh

  cp cudnn/include/* /usr/local/cuda/include
  cp cudnn/lib/* /usr/local/cuda/lib64

set your GPU in persistence mode
................................

.. code:: tcsh

  /usr/bin/nvidia-smi -pm 1

