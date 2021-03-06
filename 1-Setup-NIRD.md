# Note
to change user access

1) `find /projects/NS9048K -uid ##### -type d -exec chmod g+rx {} \;`
2) `find /projects/NS9048K -uid ##### -exec chmod g+r {} \;`

'#####' må erstattes med den enkeltes uid (finnes ved å kjøre kommandoen 'id' )
og deretter vil 1) finne alle mapper denne eier og åpne for lesing. 2) gjøre
tilsvarende med alle filer.

Eventuelt
`chmod -R g+rwx mappenavn`
`chgrp ns9048k -R <mappenavn>`


# Register to get access to NIRD

Our NIRD account have the project number: NS9048K

Register for an account here:

https://www.metacenter.no/user/application/form/norstore/

Or ssh: nird_username@login.nird.sigma2.no.

PS! It might take a couple of days before your account is ready for use.

-----------------------------

# Set up ssh public key authentication
For password-free access to Nird
## Mac/Linux:
```
# generate private/public keys (skip this if you already have ~/.ssh/id_rsa and ~/.ssh/id_rsa.pub files)
$ ssh-keygen -t rsa
# copy public key (do NOT distribute private key!)
$ scp .ssh/id_rsa.pub <nird-username>@login.nird.sigma2.no:.ssh/.
# login to Nird:
ssh <nird-username>@login.nird.sigma2.no
# add public key to .ssh/authorized_keys file
cat .ssh/id_rsa.pub >> .ssh/authorized_keys
# remove write access
chmod 400 .ssh/authorized_keys
chmod 500 .ssh 
# logout ...
```
##  Windows
(to be added)

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
 - Host: login.nird.sigma2.no
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

    ssh nird_username@login.nird.sigma2.no

To mount the disk on Linux, you need to install SSHFS and mount our project folder on Norstore to /media/norstore.

    sudo mkdir /media/nird/
    sudo chown $USER:$USER /media/nird/
    sudo apt install sshfs
    sshfs nird_username@login.nird.sigma2.no:/projects/NS9048K/ /media/nird/

Remember to replace "nird_username" with your username at NIRD and also use your NIRD password. 

## Mounting on MacOS
   
    # Create a folder in $HOME folder (if it doesn't exist)
    mkdir ~/.local
    mkdir ~/.local/bin

    # Add the line below to the file ~/.profile (or similar file):
    export PATH="~/.local/bin:/opt/local/bin:/opt/local/sbin:$PATH"

    # apply changes
    source ~/.profile

    # set up a little executable script that will create the command "mount_nird" to mount nird as the 
    # folder $HOME/nird.
    printf '#!/bin/bash\nmkdir $HOME/nird\nchown $USER $HOME/nird\nsshfs nird_username@login.nird.sigma2.no:/projects/NS9048K/NORSTORE_OSL_DISK/NS9048K $HOME/nird' >> ~/.local/bin/mount_nird
    chmod +x ~/.local/bin/mount_nird

    # to unmount nird, simply type:
    umount ~/nird

    # NOTES: the procedure may require that you install sshfs first, try doing that using e.g., homebrew or macports

### More information about Norstore

Norstore Wiki on UiO 
  https://wiki.uio.no/mn/geo/geoit/index.php/Category:Norstore