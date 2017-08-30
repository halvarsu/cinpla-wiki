# Note
to change user access

1) `find /projects/NS9048K -uid ##### -type d -exec chmod g+rx {} \;`
2) `find /projects/NS9048K -uid ##### -exec chmod g+r {} \;`

'#####' må erstattes med den enkeltes uid (finnes ved å kjøre kommandoen 'id' )
og deretter vil 1) finne alle mapper denne eier og åpne for lesing. 2) gjøre
tilsvarende med alle filer.

Eventuelt
`chmod -R g+rwx mappenavn`


# Register to get access to NIRD

Our NIRD account have the project number: NS9048K

Register for an account here:

https://www.metacenter.no/user/application/form/norstore/

Or ssh: nird_username@login.nird.sigma2.no.

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
 - /projects/NS9048K/
 - Drive letter: W:
 - Mount at login: choose for your self
 - Mount FOlder: leave blank
 - Proxy Type: None

press Save and then Mount - your drive should now be mounted

WinSshFS.exe must be placed in the Startup folder in order for norstore to be mounted at startup

## Mounting on Linux

You may want to test the connection to Norstore first (replace uiousername with your username at UiO):

    ssh uiousername@login.nird.sigma2.no

To mount the disk on Linux, you need to install SSHFS and mount our project folder on Norstore to /media/norstore.

    sudo mkdir /media/nird/
    sudo chown $USER:$USER /media/nird/
    sudo apt install sshfs
    sshfs nird_username@login.nird.sigma2.no:/projects/NS9048K/ /media/nird/

Remember to replace "nird_username" with your username at NIRD and also use your NIRD password. 

### More information about Norstore

Norstore Wiki on UiO 
  https://wiki.uio.no/mn/geo/geoit/index.php/Category:Norstore