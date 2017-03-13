perl modules
============

.. image:: /images/perl.jpg
  :scale: 50 %
  
Web references
..............

http://www.cpan.org/modules/INSTALL.html

http://search.cpan.org/~ulpfr/Math-Matrix-0.8/Matrix.pm

cpanm
.....

.. code:: tcsh

  cpan App::cpanminus

or

.. code:: tcsh

  apt-get install cpanminus

installing new modules
......................

.. code:: tcsh

  cpanm Math::Matrix
  
quaternion modules
..................

http://search.cpan.org/~jchin/Math-Quaternion-0.02/lib/Math/Quaternion.pm

converting matrix to quaternion
...............................

http://www.cg.info.hiroshima-cu.ac.jp/~miyazaki/knowledge/teche52.html

exif tools
..........

http://www.sno.phy.queensu.ca/~phil/exiftool/

http://www.sno.phy.queensu.ca/~phil/exiftool/install.html#Unix

http://phototour.cs.washington.edu/focal.html

print colors
............

http://stackoverflow.com/questions/2445605/how-can-i-get-colored-output-with-printf-and-perls-termansicolor

.. code:: tcsh

  use Term::ANSIColor qw(:constants);
  print RED, "Stop!\n", RESET;
  print GREEN, "Go!\n", RESET;
  
JSON module
...........

http://search.cpan.org/~makamaka/JSON-2.90/
http://blog-en.openalfa.com/how-to-read-and-write-json-files-in-perl
http://stackoverflow.com/questions/15653419/parsing-json-file-using-perl

.. code:: tcsh

  cpanm JSON