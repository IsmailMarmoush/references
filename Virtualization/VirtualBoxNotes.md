## Information

* `pkill -f VBoxClient`
* `VBoxClient --clipboard`

For Mac sharing folder

```
sudo apt-get install gcc make perl
cd /opt/VBoxGuestAdditions-*/init  
sudo ./vboxadd setup

sudo reboot

```

```
VBoxManage modifyhd <absolute path including the name and extension> --resize 50000

VBoxManage setextradata <vmname> "VBoxInternal/Devices/VMMDev/0/Config/GetHostTimeDisabled" "1"

# To be able to use usb from the guest machine:
sudo adduser YOURUSERNAME vboxusers # Then log out and log in again.

```

Some Good References:

* http://www.jeremychapman.info/cms/get-usb-working-in-virtualbox-under-debian-and-ubuntu
* http://www.dedoimedo.com/computers/virtualbox-usb.html
* http://community.linuxmint.com/tutorial/view/208
* http://archive.news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml
* http://www.cyberciti.biz/faq/linux-list-users-command/
* http://askubuntu.com/questions/150887/sound-from-both-headphones-and-speakers
* http://kvz.io/blog/2007/08/01/make-iso-images-on-linux/
* http://askubuntu.com/questions/147800/ripping-dvd-to-iso-accurately

## Debian as Guest

```
sudo apt-get install linux-headers-$(uname -r)
# insert guest additions cd
sudo sh VBoxLinuxAdditions.run
sudo mount -o uid=1000,gid=1000 -t vboxsf vmshared ~/vmshared/
```

Troubleshooting Q: I get a protocol error when mounting. Q: I get the error /sbin/mount.vboxsf: mounting failed with the
error: No such device. A: You mount the SF on a mount point with the same name as the share itself, change the name or
mount point. A: You're sharing a personal folder like your Home Folder (Linux), or My Documents (Windows) on the Host.
Define a new share, like a sub folder.

Q: I get an error "Unexpected error: Text file busy." when trying to edit a file. A: When using gedit, this can happen
on shared folders. This is a bug in gedit, not VB. Use a different editor.

https://forums.virtualbox.org/viewtopic.php?t=15868

```
VBoxManage list vms
VBoxManage list natnetworks
# To show rules
VBoxManage showvminfo myserver | grep 'Rule'
```

## Networking

```
# Create port forwarding rule
# e.g for access through `ssh -p 3022 deb01@127.0.0.1`
VBoxManage modifyvm <vmname> --natpf1 "ssh,tcp,127.0.0.1,3022,,22"
```

## Internal networking between vms

First define eth1 and have it internal networking then in the vm /etc/network/interfaces add the following

```
# The 192.168.56.1 is the vboxnet0 addrss
auto eth1
iface eth1 inet static
address 192.168.56.5
network 192.168.56.0
broadcast 192.168.56.255
netmask 255.255.255.0
```

## References

[ssh to virtualbox externally](http://stackoverflow.com/questions/5906441/how-to-ssh-to-a-virtualbox-guest-externally-through-a-host)
[Reference 2](http://it-ovid.blogspot.com.eg/2012/10/virtual-box-headless-cheatsheet.html)
