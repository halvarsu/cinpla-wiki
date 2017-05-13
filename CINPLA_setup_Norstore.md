# Note
to change user access
`chmod -R g+rwx mappenavn`


# Register to get access to Norstore

Our Norstore account have the project number: NS9048K

Register for an account here:

https://www.metacenter.no/user/application/form/norstore/

Or ssh: uiobrukernavn@login.norstore.uio.no.

PS! It might take a couple of days before your account is ready for use.

-----------------------------

# Mounting the disk

## Mounting on Windows

### Short version 
Install ssh windows tools and use the disk letter: W
https://github.com/dimov-cz/win-sshfs/releases

### Step by step procedure:  

install dokan 0.7.4 https://github.com/dokan-dev/dokany/releases/tag/v0.7.4

install sshfs 1.5.12.8 https://github.com/Foreveryone-cz/win-sshfs/releases/tag/1.5.12.8
 - open WinSshFS.exe
 - velg Virtual drive X:
 - press Add
 - on the left side you can now fill in information
 - Drive name: norstore
 - Host: login.norstore.uio.no
 - Port: 22
 - Username: username
 - Password: password
 - /norstore_osl/projects/NS9048K/
 - Drive letter: W:
 - Mount at login: choose for your self
 - Mount FOlder: leave blank
 - Proxy Type: None

press Save and then Mount - your drive should now be mounted

WinSshFS.exe must be placed in the Startup folder in order for norstore to be mounted at startup

## Mounting on Linux

You may want to test the connection to Norstore first (replace uiousername with your username at UiO):

    ssh uiousername@login.norstore.uio.no

To mount the disk on Linux, you need to install SSHFS and mount our project folder on Norstore to /media/norstore.

    sudo mkdir /media/norstore/
    sudo chown $USER:$USER /media/norstore/
    sudo apt install sshfs
    sshfs norstore_username@login.norstore.uio.no:/norstore_osl/projects/NS9048K/ /media/norstore/

Remember to replace "norstore_username" with your username at Norstore and also use your Norstore password. 

### More information about Norstore

Norstore Wiki on UiO 
  https://wiki.uio.no/mn/geo/geoit/index.php/Category:Norstore