# Mounting on Linux

```shell
sudo mkdir /media/ibv-hafting
sudo chown $USER:$USER /media/ibv-hafting
sudo apt install sshfs
sshfs username@nansen.uio.no:/net/lagringshotell/uio/lagringshotell/ibv-hafting/ /media/ibv-hafting
```
Suggestion for aliases
```
alias nird_mount='sshfs username@login.nird.sigma2.no:/projects/NS9048K/NORSTORE_OSL_DISK/NS9048K/server /media/nird/'
alias nird_umount='sudo umount /media/nird'
alias ibv-hafting_mount='sshfs username@nansen.uio.no:/net/lagringshotell/uio/lagringshotell/ibv-hafting/ /media/ibv-hafting'
alias ibv-hafting_umount='sudo umount /media/ibv-hafting'
```
