LDAP Administration
===================

.. image:: /images/ldap.png

LDAP users and groups:

all ldap configuration has to be done as root on **serenity**. 

.. code:: tcsh

  ssh root@serenity
 
Creating a user account
.......................

To create an account, simply use the command: 

.. code:: tcsh
 
  /shared/sbin/create-user username

*You will be asked twice to input the password for the new user. This command also creates basic structure for windows user profile.*

Changing user password
......................

To change a user's password, input the following command:

.. code:: tcsh

  smbldap-passwd -s username

*As for user's creation, you will need to input the password twice.*

Manage group memberships
........................

For adding a user into a group, two situations are possible, either we want to add all the groups for a specfic user.(all previous groups will be overwritten)

.. code:: tcsh

  smbldap-usermod -G group1,group2,group3,group4 username

Or we want to add a group without overwritting existing groups.

.. code:: tcsh

  smbldap-usermod -G +group1,group2 username
  
*(Here, group1 and group2 will be added to User while keeping any groups previously added)*

If we want to remove access to a group, the command is: 

.. code:: tcsh

  smbldap-usermod -G -group1,group2 username
  
Deleting an account
...................

To delete an account, input the following command:

.. code:: tcsh

  smbldap-userdel username
  
Reactualise after modification
..............................

For any changes to be taken into account, we need to re actualise ldap. To do so:

.. code:: tcsh

  nscd -i group