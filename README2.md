# Using GitHub for your project journal and Installing Apache web server 

Since you are reading this on GitHub you have probably already created a GitHub account.
If you haven't you can instructions for creating your account at this link

https://docs.github.com/en/get-started/onboarding/getting-started-with-your-github-accounthttps://docs.github.com/en/get>

Once you've created your GitHub account, create your first repository. You can find
instructions for doing that at this link
https://docs.github.com/en/get-started/quickstart/create-a-repo


## To configure GIT on your localhost use the following commands:

- git config --global user.name "Firstname Lastname"

- git config --global user.email "emailaddress"

- git config --global core.editor nano

- git config --global init.defaultBranch main

To confirm the information that you entered type

  git config list

###  Next configure a SSH key for this repos by using the following command

- Switch to your home directory and enter the following command

- ssh-keygen -t ed25519 -C "your emailaddress"

- press enter to accept the default file location

- press enter twice to leave passphrase blank

Your public and private keys will be created

Go to the newly created .ssh directory to view your keys

Open your public key file using nano and copy it to notepad.  Make sure that you copy all of it

Go into your profile settings on GitHub

Go to SSH settings and create a new key

Paste in your public key info and save

Go back to your GitHub repository and click on CODE

copy your SSH URL

Switch back to your repos directory and use the "git clone" command to mirror your Git Hub

 git clone "your SSH URL"


### Use these commands to update your notes on GitHub

 - git add README.md

 - git commit -m "updated README.md"

 - git push origin main


Bookmark the site [ Markdown Cheatsheet](https://www.markdownguide.org/cheat-sheet/)

-------

## Installing Apache Web Server
 

Before installing Apache check for updates to Ubuntu to make sure that you are running the latest version

Use the commands:

sudo apt update

sudo apt -y upgrade


For this class we installed the Apache2 package.  The package that You're interested in happens to be named apache2 on Ubuntu. This package name is not 

a given. On other distributions, like Fedora, the Apache package is called httpd. To learn more about the apache2 package, read about it with the apt 

show command:
	
apt show apache2


Once you've confirmed that apache2 is the package that you want, install it with the apt install command. 

sudo apt install apache2

Press Y to agree to continue after running the command below:



Use systemctl to acquire some info about apache2 and make sure it is enabled and running:

The command  

systemctl list-unit-files apache2.service

should show that apache2 is enabled and will start running automatically when the computer gets rebooted.


Check the status using this command: 

systemctl status apache2

The output of this command shows that apache2 is active, which means that it has started working.


### Viewing the Default Web Page
	
There are two ways you can look at the default web page. 

you can use a command line web browser like w3m.

OR 

you can view the site by entering the IP address of the server in our desktop browser URL bar.

	
To view your page with w3m you will need to install it it.  Use the command

sudo apt install w3m

Once it's installed, you can visit our default site using the loopback IP address (aka, localhost). 

From the command line on our server, you can run either of these two commands:

- w3m 127.0.0.1

- w3m localhost

	
	you can also get the subnet/private IP address using the ip a command, and then use that with w3m. 
	
	For example, if ip a showed that my NIC has an IP address of 10.0.1.1, then I could use w3m with that IP address:

w3m 10.0.1.1

If the apache2 package  installed and started correctly, you should see the following text at the top of the screen:

Apache2 Ubuntu Default Page
It works!

To exit w3m, press q and then y to confirm exit.

To view the default web page using a regular web browser, like Firefox, Chrome, Safari, Edge, or etc., you need to get your server's public IP address. To do that, log into the Google Cloud Console. In the left hand navigation panel, hover your cursor over the Compute Engine link, and then click on VM instances. You should see your External IP address in the table on that page. You can copy that external IP address or simply click on it to open it in a new browser tab. Then you should see the graphical version of the Apache2 Ubuntu Default Page.

Note that most browsers try to force HTTPS mode, and they also often hide the protocal from the URL. 

If your web page is not loading, make sure your URL is http://IP-ADDRESS and not https://IP-ADDRESS.



