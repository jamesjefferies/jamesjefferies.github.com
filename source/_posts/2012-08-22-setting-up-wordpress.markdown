---
layout: post
title: "Setting up WordPress"
date: 2012-08-22 15:07
comments: true
categories: 
- Techie

---

So, your server is set up and raring to go. Please see my [earlier blogpost](http://jamesjefferies.com/2012/08/22/setting-up-a-fresh-debian-server/) on getting the server to this point.. next!

## Install Apache2
Let's get our web server up and running by installing apache

```
apt-get install apache2
```

and check it is up and running with ```http://123.456.789.012``` in your friendly web browser.

## Configure Apache2 for low memory usage
With previous virtual servers, I've found that Apache needs a bit of tweaking to support WordPress load. I found this useful [post](http://imperialwicket.com/tuning-apache-for-a-low-memory-server-like-aws-micro-ec2-instances) about tweaking apache. The nuts and bolts are to amend some of the settings in your ```/etc/apache2/apache.conf``` as follows:

```
Timeout 30
KeepAlive On
MaxKeepAliveRequests 50
KeepAliveTimeout 10

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
```

## Setting up virtual host with apache

A very simple set up would be to create the following ```/etc/apache2/sites-available/myacedomainname.com``` 

```
#Ensure that Apache listens on port 80
#Listen 80 (note uncomment this with ports.conf set to 80 and you will experience a WORLD of pain!)

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
DocumentRoot /var/www/myacedomainname.com
ServerName www.myacedomainname.com

# Other directives here

</VirtualHost>
```

## Enable site (and other useful commands)

Create that file in sites-available and use the following commands to enable/disable - they will give you options when they run as to which sites you want to enable/disable

```
sudo a2ensite
sudo a2dissite
```

Force reload configuration?
```
sudo  /etc/init.d/apache2 force-reload
```

## Install PHP

Ok, well to get WordPress running, we're going to need some PHP, so get it installed

```
apt-get install php5 libapache2-mod-php5
```

## Install MySQL

And we'll need a database too

```
apt-get install mysql-server mysql-client php5-mysql
```

If already installed, but you want to reset it so you can set root password etc, give it a bit of this:

```
sudo dpkg-reconfigure mysql-server-5.1
```

## Migrating a site from another provider

### Database gubbins

Get a database dump from your old site, either using PHPMyAdmin if installed, or doing a dump from the command line using ```mysqldump```. Hopefully at the end of that process you'll be able to import the dump in to your new set up with a bit of:

```
mysql -uroot -p < databasedump.sql
```
The dump may contain a create database statement to create the database, right at the top along the lines of
```
CREATE DATABASE `db1234` DEFAULT CHARACTER SET latin1 COLLATE latin1_german2_ci; USE db1234;
```
Now you'll need to create a database user for WordPress to use. So make sure you've got a file dump of your WordPress installation, either by command line, or the hosting admin suite, or an FTP application or whatever you're comfortable with. You're going to need your wp-config.php file which will tell you how your existing WordPress site is set up. This is the bit you need to look at for now

```
/** The name of the database for WordPress */
define('DB_NAME', 'db1234');

/** MySQL database username */
define('DB_USER', 'dbuser');

/** MySQL database password */
define('DB_PASSWORD', 'dbpassword');

/** MySQL hostname */
define('DB_HOST', 'localhost');

/** Database Charset to use in creating database tables. */
define('DB_CHARSET', 'utf8');

/** The Database Collate type. Don't change this if in doubt. */
define('DB_COLLATE', '');
```

So in your existing set up you have a database user called ```dbuser``` with password ```dbpassword``` so create that user in your new setup as follows

```
grant all on db1234.* to 'dbuser'@'localhost' identified by 'dbpassword';
```

Then make sure it works with a bit of ```mysql -udbuser -Ddb1234 -p``` enter your password and hopefully you are in.

### Filesystem

Now get that dump of the filesystem you have and unpack it in ```/var/www/myacedomain.com``` or whatever you set in your virtual hosts configuration earlier. You may need to change the ownership of everything, including that directory to www-data with a bit of 

```
sudo chown -R www-data:www-data /var/www/myacedomain.com
``` 
and check the permissions too, directories should be set to 755 and files to 644. You can enforce this with 

```
sudo find . -type f -print | sudo xargs chmod 644  # Files
sudo find . -type d -print | sudo xargs chmod 755  # Directories
```

It is entirely possible that after all this, you can now hit ```http://myacedomain.com``` or ```http://123.456.789.012``` and see your migrated WordPress site!

### UTF-8 issues

Now, one issue I've had in the past is problems with UTF-8 conversion. I.e. the posts you've migrated end up with funny characters like â€“ â€œ â€™ â€ - you can tell if this is causing you grief because you see the characters mixed up in your posts, but if you comment out these lines (by adding // in front) in your WordPress config, then they.. ahem, magically go away

```
define('DB_CHARSET', 'utf8');
define('DB_COLLATE', '');
```
Best not to do that though, you *can* use the [search and replace](http://wordpress.org/extend/plugins/search-and-replace/) WordPress plugin to replace all the dodgy characters in the database. Find "â" and replace with "" - hooray!





























