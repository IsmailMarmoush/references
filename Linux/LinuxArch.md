## Linux Arch

### Disk definition using parted

```
########## Table
mktable gpt

mkpart esp fat32 1Mib 300Mib
set 1 boot on

mkpart primary ext4 314mib 200gib

mkpart primary linux-swap <>gib <>gib

mkpart primary ext4 100%
```

### Format

```
mkfs -t vfat -F 32 /dev/sda1

mkfs -t ext4 /dev/sda2
e2label /dev/sda2 A_ROOT

mkfs -t ext4 /dev/sda4
e2label /dev/sda4 A_HOME

mkswap -L A_SWAP /dev/sda3
swapon /dev/sda3
```

### Check labels

```
ls -l /dev/disk/by-label
```

### Mounting Disks

```
####### ESP
mkdir /mnt/esp
mount /dev/sda1 /mnt/esp

####### Root
mount /dev/sda2 /mnt

####### Home
mkdir /mnt/home
mount /dev/sda4 /mnt/home
```

### Installation

```
########### Preparation
wifi-menu
pacstrap /mnt base base-devel

genfstab -L /mnt > /mnt/etc/fstab
cat /mnt/etc/fstab

arch-chroot /mnt /bin/bash

######## EFI
pacman -S dialog wpa_supplicant refind-efi
mkdir -p /mnt/esp/EFI/Boot
cp /usr/share/refind/refind_x64.efi /mnt/esp/EFI/Boot/bootx64.efi
cp -r /usr/share/refind/drivers_x64/ /mnt/esp/EFI/Boot/
# echo 'extra_kernel_version_strings linux-git,linux-lts,linux;' > /esp/EFI/Boot/refind.conf

########## Locale
nano /etc/locale.gen # search for en_US UTF-8
locale-gen
echo "LANG=en_US.UTF-8" > /etc/locale.conf

########## Time
ln -sf /usr/share/zoneinfo/Europe/Berlin /etc/localtime
hwclock --systohc --utc


########## Users and passwords
######## Root
passwd

######### Sudo group
pacman -S sudo
groupadd sudo
getent group

############# User
useradd -m -G sudo -s /bin/bash heisenberg
sudo usermod -g sudo heisenberg
nano /etc/sudoers
# Then remove comment over sudo group
passwd heisenberg


########## Networking
## Create the hostname(5) file:
/etc/hostname
castle
Consider adding a matching entry to hosts(5):
/etc/hosts
127.0.0.1	localhost.localdomain	localhost
::1		localhost.localdomain	localhost
127.0.1.1	castle.localdomain	castle

systemctl enable dhcpcd

ip link # list all interfaces
ip link set <wireless interface name> down
netctl start profile



### Packages

sudo pacman -S xorg xorg-xinit i3 dmenu wget git openssh nautilus  pavucontrol terminator geany vlock i3lock xautolock gparted htop file-roller ecryptfs-utils ntp bash-completion firefox chromium
pacman -S dosfstools ntfsprogs
#### I3
nano .xinitrc 
## Add the following
#!/bin/sh
exec i3

#### Git clone home
git clone git@github.com:IsmailMarmoush/home.git
mkdir ~/.logs

### AUR
https://archlinux.fr/yaourt-en
git clone https://aur.archlinux.org/package-query.git
cd package-query
makepkg -si
cd ..
git clone https://aur.archlinux.org/yaourt.git
cd yaourt
makepkg -si
cd ..

#### Expressvpn
```

gpg --recv-key AFF2A1415F6A3A38

```

#### Time
```

timedatectl set-ntp true sudo ntpdate pool.ntp.org sudo systemctl restart ntpd

```

#### Font
```

sudo pacman -S ttf-dejavu ttf-droid ttf-fira-mono ttf-linux-libertine ttf-roboto ttf-ubuntu-font-family ttf-inconsolata
ttf-freefont ttf-hack ttf-anonymous-pro sudo cp Downloads/font/* /usr/share/fonts/ fc-cache -vf

```


## References
* https://www.ostechnix.com/install-arch-linux-latest-version/
* https://wiki.archlinux.org/index.php/installation_guide
* https://wiki.archlinux.org/index.php/GNU_Parted#UEFI.2FGPT_examples
* https://www.tecmint.com/change-modify-linux-disk-partition-label-names/
* https://wiki.archlinux.org/index.php/General_recommendations
* https://wiki.archlinux.org/index.php/User:Soloturn/Quick_Installation_guide_UEFI
* https://www.tecmint.com/change-modify-linux-disk-partition-label-names/
* https://unix.stackexchange.com/questions/14165/list-partition-labels-from-the-command-line
* http://www.hostingadvice.com/how-to/linux-add-user-to-group/
