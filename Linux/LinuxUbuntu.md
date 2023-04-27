# Ubuntu

# Ubuntu + I3+Nautilus has to use --no-desktop, so instead

gsettings set org.gnome.desktop.background show-desktop-icons false

## Generic Configuration

```
# Disable ssh from outside
echo "SSHD: ALL" >> /etc/hosts.deny
```

## DNS Name

https://wiki.archlinux.org/index.php/dnsmasq

```
sudo apt-get install dnsmasq

# Adding nameservers to /etc/dnsmasq.conf
sudo su -
echo "server=8.8.8.8" > /etc/dnsmasq.conf
echo "server=8.8.4.4" >> /etc/dnsmasq.conf

sudo service dnsmasq restart
sudo service network-manager restart

nmcli device show <interfacename> | grep IP4.DNS

sudo apt-get install ldnsutils inetutils-traceroute

```

## WIFI password

```
sudo geany /usr/share/nm-applet/ce-page-wifi-security.ui 
# line 55 to false
```

## Bluetooth Keyboard (didn't work)

```
sudo systemctl start btkbd.service 
hcitool dev
sudo cp linux/ubuntu/btkbd.conf /etc/btkbd.conf 
sudo cp linux/ubuntu/btkbd.service /etc/systemd/system/btkbd.service 
sudo cp linux/ubuntu/10-local.rules /etc/udev/rules.d/10-local.rules 
```

###### ####### Bluetooth

rfkill unblock bluetooth
