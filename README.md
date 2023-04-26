# Notes on System Librarianship

This is my journal from a course on Systems Librianship conducted by University of Kentucky Professor Sean Burns. 
They were entered using the Nano text editor.

>This journal covers:

- configuring  a Virtual Machine(VM) using Ubuntu

- building a LAMP stack server (Linux, Apache, MySQL, PHP) to create a web server similar to those used to run content management systems and integrated library systems. 

- creating a bare bones OPAC and catalogue

- installing Wordpress, Omeka and Koha

- and finally creating a demo library system architecture  


It you decide to take this course or try this project on your own, I highly recommend 

- updating your GitHub journal regularly and, 

- keeping a journal on your desktop just in case you have to rebuild your server. One of my favorite applications
 for coding and saving notes is Notepad++   I like Notepad++ for working with code because your lines are number 
and your can open multiple text files simultaneously.

- bookmarking the documentation sites for Google Cloud, Apache, Ubuntu and mySQL.


## Configuring a VM 

There's an option for creating a free or relatively inexpensive VM on Google Cloud.

To learn more visit the following links:

[An Overview of the Google Cloud Platform](https://cloud.google.com/docs/overview}

[Installing the Google Cloud CLI]( https://cloud.google.com/sdk/docs/install-sdk)

For this course we created VMs running Ubuntu 20.4.  

Our preferred method for connectng to the VM was SSH via the Google Cloud SDK shell. The command is formatted like this:

gcloud compute ssh --zone "zone-info" "name-info" --project "project-id"
   

## To keep the Ubuntu OS updated use these commands ---

	sudo apt update

	sudo apt -y upgrade

	sudo apt autoremove

	sudo apt clean  


** To reboot a VM after an OS update, use any one of the following commands:**

    sudo reboot.

    sudo shutdown -r now This will perform a system shutdown in a proper way and then reboot the computer.
	
** To shutdown a VM ** 

    sudo init 6.

    sudo poweroff.

    sudo shutdown -h now This will perform a system shutdown in a proper way. ...

    sudo halt is another way to shutdown.

    sudo init 0.


## Frequently used Linux commands


apt show "package name"

sudo su (to get to the root directory as an admin)

cd to change directories

"cd .." command to go back on directory level

Use mkdir to make directories 

"rm -r" command to delete non-empty directories. During this process you will add, move, and copy several directories.  
Deleting directories created by mistake will save disk space. 
 
----------------------------

 
## A few basic MySQL commands

- to log on type the command "mysql -u yourusername -p

- to create a database type "create database databasename;"

- to set database privileges type "grant all privileges on databasename to 'yourusername'@'localhost';"

- to see a list of databases type "show databases;"

- to exit mysql and return to the Linux prompt type "\q"

- to use a database type "use databasename;"

- to create a table type a command like this
 
"create table tablename

(id int unsigned not null auto_increment, 

variablename varchar(150) not null,

variablename varchar(150) not null, 

variable date not null,

primary key (id)

);"

- to add records to a table type a command similar to this 

"insert into table name (variablename1, variablename2, variablename3) values

('variable1', 'varialble2', 'varialble3');

- to display table information type a command like this

"select * from tablename;
 

---

Go to README2.md for more 
