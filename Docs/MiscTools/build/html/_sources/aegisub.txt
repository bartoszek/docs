Aegisub Subtitle Generator
==========================

.. image:: /images/aegisub.png

Web References
..............

http://www.aegisub.org/

install version 3.2
...................

http://forum.aegisub.org/viewtopic.php?f=10&t=66167

.. code:: tcsh

  add-apt-repository ppa:djcj/aegisub
  apt-get update
  apt-get install aegisub
  apt-get install aegisub-unstable
  
use dictionaries
................

Options/Interface/chemin des dictionnaires 

.. code:: tcsh

  /usr/share/hunspell
  
burn subtitles on video
.......................

https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo

.. code:: tcsh

  ffmpeg -i video.avi -vf "ass=subtitle.ass" out.avi

Docs
....

http://docs.aegisub.org/

http://docs.aegisub.org/3.2/Main_Page/

dictionaries
............

https://wiki.mozilla.org/L10n:Dictionaries

Building Aegisub
................

http://devel.aegisub.org/wiki/Build/Unix

Wiki
....

http://devel.aegisub.org/wiki

Subtitles formats
.................

http://devel.aegisub.org/wiki/SubtitleFormats

Tutorial
........

http://sub.wordnerd.de/linux-subs.html

