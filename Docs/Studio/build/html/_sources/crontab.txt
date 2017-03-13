Using Crontab
=============

Web references
..............

https://help.ubuntu.com/community/CronHowto

editing crontab
...............

.. code:: tcsh

  crontab -e
  
usage
.....

Each of the sections is separated by a space, with the final section having one or more spaces in it.

minute (0-59), hour (0-23, 0 = midnight), day (1-31), month (1-12), weekday (0-6, 0 = Sunday), command

.. code:: tcsh

  01 04 1 1 1 /usr/bin/somedirectory/somecommand
  
will run /usr/bin/somedirectory/somecommand at 4:01am on January 1st plus every Monday in January. An asterisk (*) can be used so that every instance (every hour, every weekday, every month, etc.) of a time period is used.

.. code:: tcsh

  01 04 * * * /usr/bin/somedirectory/somecommand
  
will run /usr/bin/somedirectory/somecommand at 4:01am on every day of every month.

It is recommended that you use the full path to the desired commands

use vi
......

.. code:: tcsh

  export EDITOR=vi
  
sendmail
........

.. code:: tcsh

  $catcmd="echo \"Subject: serenity cron $date\" | cat - $logfile | /usr/sbin/sendmail luc.froehlicher\@alamaison.fr";

