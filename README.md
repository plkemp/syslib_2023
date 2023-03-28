# Notes on System Librarianship

These are notes from a course on Systems Librianship conducted by Prof. Sean Burns. They were entered using the Nano text editor.

>This journal covers:

- configuring  a Virtual Machine(VM) using Ubuntu

- building a LAMP stack server (Linux, Apache, MySQL, PHP) to create a web server similar to those used to run content management systems and integrated library systems. 

- creating a bare bones OPAC and catalogue

- installing Wordpress, Omeka and Koha 


## Confiuring a VM 

There's an option for creating a free or relatively inexpensive VM on Google Cloud.

To learn more visit the following links:

-[An Overview of the Google Cloud Platform](https://cloud.google.com/docs/overview}

-[Installing the Google Cloud CLI]( https://cloud.google.com/sdk/docs/install-sdk)

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



##  Notes on Using GitHub with Linux

 Use the "git clone" command to mirror your Git Hub

 Use the "cd -" command to go back on directory level

 Use the "rm -r" command to delete non-empty directories when you make a mistake
 
----------------------------

[ Markdown Cheatsheet](https://www.markdownguide.org/cheat-sheet/)
 
 Use these commands to update your notes on GitHub
 notes added 03-04-23

 - git add README.md
 
 - git commit -m "updated README.md"

 - git push origin main 





 
## A few basic mySQL commands

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
 

