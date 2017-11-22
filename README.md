# SDM



Web Server Installation

sudo apt-get install tasksel

sudo tasksel

To test, open web browser and enter localhost.

the web root, in other words the location where the content is locacted, is /var/www/html.

If you want to change the location to a different one:

https://www.digitalocean.com/community/tutorials/how-to-move-an-apache-web-root-to-a-new-location-on-ubuntu-16-04

If the location is a mounted drive, make sure that the location has permissions that allow access for the web server:

sudo chmod 755 /mnt/data

If you have problems, it helps to look a tt he error log at /var/log/apache2/error.log

if you prefer a graphical editor in superuser mode:
SUDO_EDITOR="gedit -w" sudoedit /etc/apache2/sites-available/000-default.conf 




Drupal installation

https://theaccidentalcoder.com/content/drupal-and-permissions-avoiding-directory-sitesdefaultfiles-not-writable-error
sudo chown www-data:www-data [path-to-my-Drupal-directory]/sites/default/files -R










