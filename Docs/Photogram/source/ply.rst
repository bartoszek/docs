ply
===

The PLY file format is a simple object description that was designed as a convenient format for researchers who work with polygonal models. Early versions of this file format were used at 
Stanford University and at UNC Chapel Hill.

A PLY file consists of a header followed by a list of vertices and then a list of polygons. The header specifies how many vertices and polygons are in the file, and also states what properties 
are associated with each vertex, such as (x,y,z) coordinates, normals and color. The polygon faces are simply lists of indices into the vertex list, and each face begins with a count of the number 
of elements in each list.

Web references
..............

http://www.cc.gatech.edu/projects/large_models/ply.html

http://www.cc.gatech.edu/projects/large_models/files/ply.tar.gz

build
.....

.. code:: tcsh

  cd ply/
  make all
