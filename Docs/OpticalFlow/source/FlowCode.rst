FlowCode - Middlebury format
============================

http://vision.middlebury.edu/flow/data/

Some utilities for reading, writing, and color-coding .flo images

See flowIO.cpp for sample code for reading and writing .flo files.
Here's an excerpt from this file describing the flow file format:

.. code:: tcsh

  // ".flo" file format used for optical flow evaluation
  //
  // Stores 2-band float image for horizontal (u) and vertical (v) flow components.
  // Floats are stored in little-endian order.
  // A flow value is considered "unknown" if either |u| or |v| is greater than 1e9.
  //
  //  bytes  contents
  //
  //  0-3     tag: "PIEH" in ASCII, which in little endian happens to be the float 202021.25
  //          (just a sanity check that floats are represented correctly)
  //  4-7     width as an integer
  //  8-11    height as an integer
  //  12-end  data (width*height*2*4 bytes total)
  //          the float values for u and v, interleaved, in row order, i.e.,
  //          u[row0,col0], v[row0,col0], u[row0,col1], v[row0,col1], ...
  //


Once you have a .flo file, you can create a color coding of it using
color_flow

Use colortest to visualize the encoding


To compile

.. code:: tcsh

  cd imageLib
  make
  cd ..
  make
  ./colortest 10 colors.png
  
exr2flo
=======

convert .exr file to colorflow format png

in ~/flow-code/tinyexr/examples/exr2flo

flo2exr
=======

convert .flo file to raw motion exr

in ~/flow-code/tinyexr/examples/flo2exr

.. code:: tcsh

  usage: ./flo2exr [-quiet] in.flo out.exr

flo2twixtor
===========

convert .flo file to twixtor normalised format motion exr

in ~/flow-code/tinyexr/examples/flo2twixtor

.. code:: tcsh

  usage: flo2twixtor [-quiet] in.flo out.exr normalisation