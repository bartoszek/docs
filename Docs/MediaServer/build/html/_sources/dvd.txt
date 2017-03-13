Install libdvdcss2
===================

Most commercial DVDs are encrypted with CSS (the Content Scramble System), which attempts to restrict the software that can play a DVD.

Web References
..............

https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs

http://askubuntu.com/questions/487949/ubuntu-14-04-and-libdvdcss-file

Install libdvdcss2
...................

note: if you have installed ubuntu-restricted-extras this has already been installed automatically for you

.. code:: tcsh

  apt-get install libdvdread4
  /usr/share/doc/libdvdread4/install-css.sh
  
Rebooting may be necessary.

transcode for K3b
..................

.. code:: tcsh

  apt-get install transcode