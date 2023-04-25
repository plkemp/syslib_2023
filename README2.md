# Using GitHub for your project Journal

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

##      Next configure a SSH key for this repos by using the following command

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



## Use these commands to update your notes on GitHub

 - git add README.md

 - git commit -m "updated README.md"
 - git commit -m "updated README.md"

 - git push origin main


Bookmark the site [ Markdown Cheatsheet](https://www.markdownguide.org/cheat-sheet/)



