Hostsharing-Ansible-Contao
==========================
This Ansible playbook will install Contao 3.5.4 on a server from www.hostsharing.net.

To use these modules we have to create a file named ".hsadmin.properties" in the home directory of the package admins. In it we have to insert the packagename and password of the package admin. 

Example:

    xyz00@h99:~$ cat .hsadmin.properties 
    xyz00.passWord=insertpkgadminpasswordhere

This file should be protected, else it would be world readable:

    xyz00@h99:~$ chmod 600 .hsadmin.properties

We clone this git-repo to our machine:

    $ git clone https://github.com/Dominic-Schlegel/Hostsharing-Ansible-Contao.git

Then we change the working directory:

    $ cd Hostsharing-Ansible-Contao

All needed parameters can be set in the inventory file now. Change xyz00 to the name of your package admin. Set the name of a new user and a password. This username and password will be used in the database installation process too (database-name & database-username: xyz00_user). Please consider changing them both (NewUser-password in HSAdmin and Database-password) after the installation. We can edit the inventory file with:

    $ vim inventory

The Option -i can be used now to read this inventory file instead of the /etc/ansible/hosts file. If we want to login with an SSH-Key instead of an SSH-Password, we have to remove the -k option from the following string. The -K is needed to prompt us once for the sudo password of the new user.

To prepare everything for the Contao installation (including a Mysql database) we run:

    $ ansible-playbook -i inventory playbook-contao.yml -k -K

Now we can reach the Contao installation script via:

    http://www.user.xyz00.hostsharing.net/contao/install.php

--- Open Source Hosting ---
 https://www.hostsharing.net
