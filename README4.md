# Installing WordPress and Omeka 

		
The WordPress installation requires at least PHP version 7.4 and MySQL version 5.7.  

To learn more about Wordpress requirements at this link https://developer.wordpress.org/advanced-administration/


You can confirm that your system meets the requirements with the following commands:

		php --version
		
		mysql --version

Our VM installtions are running PHP 7.4.3 and MySQL 8.0 but we need to add additional PHP modules in order to allow WordPress to 

operate at full functionality.  You can install these using the apt command:

	sudo apt install php-curl php-xml php-imagick php-mbstring php-zip php-intl

Then restart Apache2 and MySQL:

	sudo systemctl restart apache2
	
	sudo systemctl restart mysql		


## Installing Wordpress

The next step is to download and extract the WordPress tar.gz file.  Tar files are similar to compressed zip files.  

This is very much like a compressed zip file. Although we only download one file, when we extract it with the tar command, 

The general instructions include:

 - Change to the /var/www/html directory.
	
 - Download the latest version of WordPress using the wget program.
	
 - Extract the package using the tar program.

 - Use the following ocmmands:

	cd /var/www/html

	sudo wget https://wordpress.org/latest.tar.gz

	sudo tar -xzvf latest.tar.gz

---------------

The WordPress documentation describes how to use phpMyAdmin to create the database and a user for WordPress. 

phpMyAdmin is a graphical front end to the MySQL relational database that you would access through the browser.  

However for this installation we created the database manually in MySQL.


Switch to the root Linux user and login as the MySQL root user by entering

	sudo su

	mysql -u root

### Create a mySQL database for Wordpress

	create user 'wordpress'@'localhost' identified by 'xxxxxxxxxx';
	
	create database wordpress;
	
	grant all privileges on wordpress.* to 'wordpress'@'localhost';
	
	show databases;
	
	\q
### Set up wp-config.php
	
Follow these general steps:

- Change to the wordpress directory, if you haven't already.

- Copy and rename the wp-config-sample.php file to wp-config.php.

- Edit the file and add your WordPress database name, user name, and password in the fields for DB_NAME, DB_USER, and DB_PASSWORD.


	cd /var/www/html/wordpress

	sudo cp wp-config-sample.php wp-config.php

	sudo nano wp-config.php

	/* Disable FTP 

	define('FS_METHOD','direct');

----

WordPress will need to write to files in the base directory. 

Whilte you're in the Wordpress directory  /var/www/html/wordpress or /var/www/html/blog or like, run the following command:

	sudo chown -R www-data:www-data *



You are ready to complete the rest of the Wordpress configuration in your browsers. 

Open your browser to 

http:// your IP address / your Wordpress directory name /wp-admin/install.php

Wordpress will walk you through the rest

Now comes the hard part.  

Choose a theme and configure it.  

If you're new to WordPress, start with a simple theme that will not require a great deal of customization.  

------------

## Installing Omeka on Linux/Unbuntu

### Omeka uses the ImageMagick suite of utilities to work with photo files. 

To install ImageMagick type the following command

	sudo apt install imagemagick

Enable Apache mod_rewrite. This is an Apache module used to rewrite URLs. 

Omeka uses this to create appropriate URLs for items and collections in its digital libraries

	sudo a2enmod rewrite

Then restart Apache

	sudo systemctl restart apache2

-------------

### Installing Omeka 

Install the unzip package in order to extract the Omeka files 

	sudo apt install unzip 

	cd /var/www/html

	sudo wget https://github.com/omeka/Omeka/releases/download/v3.1/omeka-3.1.zip

	sudo unzip omeka-3.1.zip 

Rename the Omeka directory

	sudo mv omeka-3.1 omeka 


-- Return to the root directory 

	sudo su

### Create a mySQL database for Omeka

	mysql -u root 

	create user 'omeka'@'localhost' identified by 'xxxxxxxxxx';     

	create database omeka;

	grant all privileges on omeka.* to 'omeka'@'localhost';

	show databases;

	\q

----

 In the extracted directory, find the db.ini file and add your database credentials, and
 
 replace all values containing XXXXXX, with the appropriate information.

	cd /var/www/html/omeka

	sudo nano db.ini  

----

Create an authentication file in our /etc/apache2 directory, which is where the Apache2web server stores its configuration files. 

The file will contain a hashed password and a username we give it.  Use the command 

	sudo htpasswd -c /etc/apache2/.htpasswd

Next you need to tell the Apache2 web server to use the htpasswd to control access to the cataloging module. 

To do that use nano to open the apache2.conf file.  Type
	
	sudo nano /etc/apache2/apache2.conf

-------

Change file ownership so Omeka can write to the directory

	sudo chown -R www-data:www-data *

-------

Check that the configuration file is okay, Type 

	apachectl configtest


If you get a Syntax OK message, then restart Apache2 and check its status --- 

	sudo systemctl restart apache2

	sudo systemctl restart mysql

-------

To access the Omeka Admin after the install go to

	http:// your IP address /omeka


### Troubleshooting Installation Errors 

If Omeka does not display the installation page after you completed the server installation you may encounter an error like

** "Omeka has encounter an error. ***
 
 To display the exact error do the following:

Go into the files for your Omeka installation on your server. 

Open the .htaccess file in the root directory of your Omeka installation, where you'll also find the plugins and themes folders.

You might need to turn on "see hidden files" in order to see the .htaccess file. If you're not sure how to do this, look in the directions for your file manager.

Find the following line, and uncomment it (that is, remove the # sign): 

#SetEnv APPLICATION_ENV development. 

When you are done, it should read SetEnv APPLICATION_ENV development.

You might need to download the file in order to edit it. 

Be sure to upload the edited version and replace the older version

----------------------------------
You may want to install a variety of themes and plugins.  

Remember to upload themes to the /Omeka/themes directory and plugins to the /Omeka/plugins directory.  

You can find a list of registered Omeka Classic plugins here https://omeka.org/classic/plugins/

You can find more at https://daniel-km.github.io/UpgradeToOmekaS/omeka_plugins.html


Occassionally plugins can cause conflicts or Omeka server errors. If that occurs, you may just need to deactivate and uninstall 

the plugin.  Unfortunately sometimes you need to reinstall Omeka.  Fortunately, you will have already installed imagemagick, 

uploaded the Omeka zip file and created a MySQL database and user.  

To reinstall Omeka, delete the Omeka directory using the commmand 

	sudo rm -r omeka 
	
	sudo unzip omeka-3.1.zip 
	
This will reinstall Omeka.  

If your problem persist you can delete and recreate the MySQL database by using the drop command 

	drop user 'username'@'localhost'

	drop database omeka
	

If you can't recall your passwords, you may need to repeat the entire Omeka installation process.  
