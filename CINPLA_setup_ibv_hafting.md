# Mounting on Linux

```shell
sudo mkdir /media/ibv-hafting
sudo chown $USER:$USER /media/ibv-hafting
sudo apt install sshfs
sshfs username@nansen.uio.no:/net/lagringshotell/uio/lagringshotell/ibv-hafting/ /media/ibv-hafting
```
Suggestion for aliases
```
alias norstore_mount='sshfs username@login.norstore.uio.no:/norstore_osl/projects/NS9048K/ /media/norstore/'
alias norstore_umount='sudo umount /media/norstore'
alias ibv-hafting_mount='sshfs username@nansen.uio.no:/net/lagringshotell/uio/lagringshotell/ibv-hafting/ /media/ibv-hafting'
alias ibv-hafting_umount='sudo umount /media/ibv-hafting'
```