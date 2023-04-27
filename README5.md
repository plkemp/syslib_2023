
# Installing KOHA

For this course we installed KOHA version 22.11.3 on a separate VM than Wordpress and Omeka 

We created a new virtual instance that has more RAM but all of the other options including the operating system 

(Ubuntu 20.04) are the same.  

After logging on to the new VM go to the root directory to begin installing Koha.

Type

	sudo su 

Add the Koha repository to our server 

	echo 'deb http://debian.koha-community.org/koha stable main' | sudo tee /etc/apt/sources.list.d/koha.list

Add the digital signature that verifies the above repository

	wget -q -O- https://debian.koha-community.org/koha/gpg.asc | sudo apt-key add -

Use the 'show" command to view the Koha package info --- 

	apt show koha-common

Install koha

	apt install koha-common



### Configure Koha ---- 

	nano /etc/koha/koha-sites.conf

In the above koha-sites.conf file, change the line that contains the following information:

	INTRAPORT="80"

	To:

	INTRAPORT="8080"

---

Next install and setup mysql-server -- 

	apt install mysql-server

	set the root MySQL password --


The Apache2 web server was installed with the Koha package 

To enable URL rewriting and CGI functionality 

	a2enmod rewrite

	a2enmod cgi 

restart Apache server -- 

	systemctl restart apache2

Next create a database for Koha --

	koha-create --create-db bibliolib

Tell Apache2 to listen on port 8080 -- 

	nano /etc/apache2/ports.conf 

And add 

	Listen: 8080

estart Apache2 -- 

	systemctl restart apache2

-- disable the default Apache2 setup --

-- enable traffic compression using deflate -- 

-- enable the bibliolib site -- 

-- reload Apache2's configurations and restart again -- 

		a2dissite 000-default

		a2enmod deflate

		a2ensite bibliolib

		systemctl reload apache2

		systemctl restart apache2

----

### Run the Koha Web Installer -- 

First, get your Koha username and password in the following file:

	nano /etc/koha/sites/bibliolib/koha-conf.xml

-----

Koha’s Plugin System allows for you to add additional tools and reports to Koha that are specific to your library. 

Plugins are installed by uploading KPZ ( Koha Plugin Zip ) packages. A KPZ file is just a zip file containing the perl files, 

template files, and any other files necessary to make the plugin work.

The plugin system needs to be turned on by a system administrator.

### Enable Koha plugins 

To set up the Koha plugin system you must first make some changes to your install.

    Change <enable_plugins>0</enable_plugins> to <enable_plugins>1</enable_plugins> in your koha-conf.xml file

Restart your webserver

On the Tools page you will see the Tools Plugins and on the Reports page you will see the Reports Plugins.


