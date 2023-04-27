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

