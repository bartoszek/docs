Primitive
=========

GitHub : https://github.com/fogleman/primitive

TwitterBot : https://twitter.com/PrimitivePic

https://rogeralsing.com/2008/12/07/genetic-programming-evolution-of-mona-lisa/

.. image:: /images/primitive3.png
  :scale: 50 %
  
.. image:: /images/primitive2.gif
  :scale: 50 %
  
.. image:: /images/primitive1.png
  :scale: 50 %
  
Install go
..........

Go Page : https://golang.org/doc/install

download binaries : https://golang.org/dl/

Install : https://golang.org/doc/install?download=go1.7.1.linux-amd64.tar.gz

untar in ~/go

in ~/.bashrc

.. code:: tcsh

  export GOROOT=$HOME/go
  export GOPATH=$HOME/gowork
  export PATH=/home/luluf/go/bin:$PATH
  
.. code:: tcsh

  cd ~
  mkdir gowork
  go get -u github.com/fogleman/primitive
  
.. code:: tcsh

  $GOPATH/bin/primitive -i ima.png -m 1 -n 100 -o tmp.png -s 900 -v
  
.. code:: tcsh

  Flag 	Default 	Description
  -i 	n/a 	input file
  -o 	n/a 	output file
  -n 	n/a 	number of shapes
  -m 	1 	mode: 0=combo, 1=triangle, 2=rect, 3=ellipse, 4=circle, 5=rotatedrect
  -r 	256 	resize large input images to this size before processing
  -s 	1024 	output image size
  -a 	128 	color alpha
  -v 	off 	verbose output