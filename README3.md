# Installing PHP and mySQL 

## Installing PHP 


PHP is the acronym for PHP: Hypertext Preprocessor.  It is a widely-used open source general-purpose scripting language that is especially suited 

for web development and can be embedded into HTML.

A basic understanding of PHP is essential for web designers.  If you are interested in learning more about how to write PHP visit 

https://www.w3schools.com/php/default.asp  and https://www.php.net/manual/en/intro-whatis.php


The main use of PHP is to interact with databases, like MySQL, MariaDB, PostgreSQL, etc., in order to create data-based page content. 


> What Can PHP Do?

 - PHP can generate dynamic page content

 - PHP can create, open, read, write, delete, and close files on the server

 - PHP can collect form data

 - PHP can send and receive cookies

 - PHP can add, delete, modify data in your database

 - PHP can be used to control user-access

 - PHP can encrypt data

 - With PHP you are not limited to output HTML. You can output images or PDF files. You can also output any text, such as XHTML and XML (PHP Introduction, n.d.)


## To install PHP on your LAMP server 

    - Install PHP and relevant Apache2 modules
	
    - Configure PHP and relevant modules to work with Apache2
	
    - Configure PHP and relevant modules to work with MySQL
	
----

Use the following commands: 

sudo apt install php libapache2-mod-php

sudo systemctl restart apache2

systemctl status apache2



To check that it's been installed and that it's working with Apache2, create a small PHP file in your web document root. 

To do that, go to the /var/www/html/ directory and create a file called info.php:

cd /var/www/html/

sudo nano info.php

In that file, add the following text, then save and close the file:

<?php
phpinfo();
?>

Now visit that file using the external IP address for your server. For example, in Firefox, Chrome, etc, go to:

http:// your server IP address /info.php


-------

By default, when Apache2 serves a web page, it looks for and serves a file titled index.html, even if it does 

not display that file in the URL bar. However, in order to serve PHP pages, we want Apache2 to default to a file 

titled index.php instead of index.html file. 


To configure that, we need to edit the dir.conf file in the /etc/apache2/mods-enabled/ directory. 

In that file there is a line that starts with DirectoryIndex. 

The first file in that line is index.html, and then there are a series of other files that Apache2 will look for in the order listed. 

If any of those files exist in the document root, then Apache2 will serve those before proceeding to the next. \

We want to put index.php first and let index.html be second on that line. 

Before modifying this file, it's good practice to create a backup of the original. 

Use the cp command to create a copy with a new name, and then use nano to edit the file.
		
cd /etc/apache2/mods-enabled/

sudo cp dir.conf dir.conf.bak

sudo nano dir.conf

		
		
Change the line to this:

DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm


Whenever you make a configuration change, use the apachectl command to check our configuration:

apachectl configtest



If you get a Syntax Ok message, we can reload the Apache2 configuration and restart the service:

- sudo systemctl reload apache2

- sudo systemctl restart apache2

---------

### Create a PHP page 

Now create a basic PHP page. cd back to the Apache2 document root directory and use nano to create and open an index.php file:

cd /var/www/html/

sudo nano index.php


They say that PHP is an easy language but it will take me a while to feel comfortable creating scripts from scratch.  Thankfully for this course 

Professor Burns provided us with PHP scripts.  

This script uses HTML and PHP to index.php that functions as a simple browser detector. 

Add the following code:

<html>

<head>

<title>Broswer Detector</title>

</head>

<body>

<p>You are using the following browser to view this site:</p>

<?php

$user_agent = $_SERVER['HTTP_USER_AGENT'];

if(strpos($user_agent, 'Edge') !== FALSE) {

    $browser = 'Microsoft Edge';
	
} elseif(strpos($user_agent, 'Firefox') !== FALSE) {

    $browser = 'Mozilla Firefox';
	
} elseif(strpos($user_agent, 'Chrome') !== FALSE) {

    $browser = 'Google Chrome';
	
} elseif(strpos($user_agent, 'Opera Mini') !== FALSE) {

    $browser = "Opera Mini";
	
} elseif(strpos($user_agent, 'Opera') !== FALSE) {

    $browser = 'Opera';
	
} elseif(strpos($user_agent, 'Safari') !== FALSE) {

    $browser = 'Safari';
	
} else {

    $browser = 'Unknown';
}

if(strpos($user_agent, 'Windows') !== FALSE) {

    $os = 'Windows';
	
} elseif(strpos($user_agent, 'Linux') !== FALSE) {

    $os = 'Linux';
	
} elseif(strpos($user_agent, 'Mac') !== FALSE) {

    $os = 'Mac';
	
} elseif(strpos($user_agent, 'iOS') !== FALSE) {

    $os = 'iOS';
	
} elseif(strpos($user_agent, 'Android') !== FALSE) {

    $os = 'Android';
	
} else {

    $os = 'Unknown';
}

if($browser === 'Unknown' || $os === 'Unknown') 

    echo 'No browser detected.';
	
} else {

    echo 'Your browser is ' . $browser . ' and your operating system is ' . $os . '.';
	
}

?>

</body>

</html>

Next, save the file and exit nano. In your browser, visit your external IP address site (again, replace your server's IP address):

http:// your IP address

Although your index.html file still exists in your document root, Apache2 now returns the index.php file instead. 

However, if for some reason the index.php was deleted, then Apache2 would revert to the index.html file since that's what is listed 

next in the dir.conf DirectoryIndex line.

-------------

## Setting Up and Configuring mySQL on a VM 

MySQL is an open-source relational database management system developed, distributed, and supported by Oracle Corporation.

The MySQL website (http://www.mysql.com/) provides the latest information about MySQL software.

> MySQL is used with other programs to implement applications that need relational database capability ( e.g.Drupal, Joomla, phpBB, and WordPress) 

and websites (e.g. Facebook, Flickr, MediaWiki, Twitter, and YouTube.)


For this course, we created databases for to store and serve data for a bare bones OPAC demo, Wordpress and Koha.  

### Install MySQL 

To install MySQL use the command 

sudo apt install mysql-server



Make sure that the database server is running by using the command 

systemctl status mysql 


Login as the root Linux user to test the database 

 - sudo su


Connect to the MySQL server as the MySQL root user 

 - mysql -u root


You can type \h for help or \c to clear the current input statement 



You can display a list of the databasess using the show command. If you haven't created any, the response msy be 0. 

However, you may see databases that were created during the installation of other programs. 

Type

show databases;

----

**IMPORTANT**  - Don't forget to end MySQL command strings with a semicolon.  

> When you type a command in mySQL without the ending semicolon MySQL won't run the command. Instead of giving an error it gives an endless list of:  

>	'>
	
>	'>
	
>	'>
	
>	'>

If this happens, break the loop by typing '\c  OR \c         

----

Reserve the root MySQL user for special use cases and instead create a MySQL user, or more than one MySQL user, as needed.
 
Create a regular MySQL user using the create command. 

From the MySQL prompt type

		create user 'username'@'localhost' identified by 'password';      (


If the prompt returns a Query OK message, then the new user should have been created without any issues. 

Now create a database

		create database databasename;
		
USe the show command to confirm that the database was created		
		
		show databases;
		
Give the user rights to access the database

		grant all privileges on databasename.* to 'username'@'localhost';


** IMPORTANT ** 

 - The regular user will be granted all privileges on the new database, including all its tables. Other than granting all privileges
 
 _ we could limit the user to specific privileges, including: CREATE, DROP, DELETE, INSERT, SELECT, UPDATE, and GRANT OPTION.
 
 _ Such privileges may be called operations or functions, and they allow MySQL users to use and modify the databases, where appropriate.
 
 _  For example, we may want to limit the opacuser user to only be able to use SELECT commands. It totally depends on the purpose of the 
 
 database and our security risks. --- 




----

PHP Introduction. (n.d.). Retrieved April 25, 2023, from https://www.w3schools.com/php/php_intro.asp

