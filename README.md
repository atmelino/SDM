# SDM



<h2>Web Server Installation on Desktop Machine</h2>

sudo apt-get install tasksel

sudo tasksel

To test, open web browser and enter localhost.

the web root, in other words the location where the content is locacted, is /var/www/html.

If you want to change the location to a different one:

https://www.digitalocean.com/community/tutorials/how-to-move-an-apache-web-root-to-a-new-location-on-ubuntu-16-04

If the location is a mounted drive, make sure that the location has permissions that allow access for the web server:

sudo chmod 755 /mnt/data

other things that might have helped:

sudo chgrp -R www-data /mnt/data

sudo usermod -a -G www-data user




If you have problems, it helps to look at the error log at /var/log/apache2/error.log




if you prefer a graphical editor in superuser mode:
SUDO_EDITOR="gedit -w" sudoedit /etc/apache2/sites-available/000-default.conf 


<h2>Web Server Installation inside Virtualbox</h2>

download server ISO from http://www.ubuntu.com

start virtualbox

create new VM

etc.

choose LAMP server and mailserver

etc.

in virtualbox click on settings for the VM, network, select bridged adapter.

on the server, type ifconfig to get the IP address of the server.

outside VM, open web browser, enter the IP address.

https://askubuntu.com/questions/237461/how-do-i-access-ubuntu-server-running-in-virtualbox-from-outside


(works for ssh but not for http:

http://blog.teamtreehouse.com/set-up-a-linux-server-on-virtualbox)

Install guest additions to make it easier to copy files (shared folders):

https://www.techrepublic.com/article/how-to-install-virtualbox-guest-additions-on-a-gui-less-ubuntu-server-host/

on host, setup a shared folder by clicking on settings (folder has to exist for OK button to be enabled) 

on guest, after reboot, folder will be at /media/sf_your_folder_name

To make it accessible to you: 

sudo usermod -a -G vboxsf your_user_name

logout and log back in

https://askubuntu.com/questions/161759/how-to-access-a-shared-folder-in-virtualbox


<h2>Web Server Installation on Digitalocean</h2>






<h2>Drupal installation</h2>

download Drupal from http://www.drupal.org

extract the file in the location where you want the web server

point a web browser to that location.

Typical errors/warnings during installation:

(1) PHP EXTENSIONS Disabled

sudo apt-get install php-gd
sudo apt-get install php-xml

(2) The directory sites/default/files is not writable

sudo chown www-data:www-data sites/default/files -R

https://theaccidentalcoder.com/content/drupal-and-permissions-avoiding-directory-sitesdefaultfiles-not-writable-error

(3) SETTINGS FILE The Settings file does not exist.

sudo chown www-data:www-data settings.php 

(4) CLEAN URLS Disabled

https://www.drupal.org/node/15365

a2enmod rewrite

change AllowOverride None to AllowOverride All



In admin mode, click on configuration.
Errors:

(1) update manager module

(2) trusted host pattern error

https://drupal.stackexchange.com/questions/145690/untrusted-host-localhost-in/145994#145994

$settings['trusted_host_patterns'] = array(
  '^example\.com$',
  '^www\.example\.com$',
  '^localhost$',
);




create new user account error

Message: "Unable to send email. Contact the site administrator if the problem persists."

