---
layout: post
title:  Setting a wired connection in Ubuntu
categories: Notes
---

## Setting a wired connection in Ubuntu 18.04

While reinstalling Ubuntu 18.04, I encountered the wired connection issue again.
(wired connection status was 'connecting' at first)

First, set the wired connection IPv4 setting to manual
- address: 192.168.0.1
- netmask: 255.255.255.0
- gateway: 192.168.0.1

Then open /etc/network/interfaces file by
```
sudo gedit /etc/network/interfaces
```

and add the following
---------------------------------------
auto enp5s0
iface enp5s0 inet static
address 147.46.112.93
netmask 255.255.255.0
gateway 147.46.112.1
dns-nameservers 168.126.63.1 8.8.8.8
---------------------------------------

then the file looks like:
---------------------------------------
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto enp5s0
iface enp5s0 inet static
address 147.46.112.93
netmask 255.255.255.0
gateway 147.46.112.1
dns-nameservers 168.126.63.1 8.8.8.8
---------------------------------------

Finally, save the file and restart the network.
```
sudo /etc/init.d/networking restart
```
