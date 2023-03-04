# Notes on System Librarianship
 
##  Notes on Using GitHub with Linux

- Use the "git clone" command to mirror your Git Hub

-  Use the "cd -" command to go back on directory level
 
-  Use the "rm -r" command to delete non-empty directories when you make a mistake
 
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
 

