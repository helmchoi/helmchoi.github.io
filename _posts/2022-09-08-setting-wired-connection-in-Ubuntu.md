---
layout: post
title:  Setting a wired connection in Ubuntu
categories: Notes
---

## Setting a wired connection in Ubuntu 18.04

While reinstalling Ubuntu 18.04, I encountered the wired connection issue again.
(wired connection status was 'connecting' at first)

First, set the wired connection IPv4 setting to manual
- address: YOUR_IP.xx
- netmask: 255.255.255.0
- gateway: YOUR_IP.1

where YOUR_IP is the first three numbers of your ip address (e.g., 192.168.0).
For example - address: 192.168.0.100, gateway: 192.168.0.1

Then open /etc/NetworkManager/NetworkManager.conf and revise to managed=true as:
```
[ifupdown]
managed=true
```

1) Open /etc/netplan/xx-network-manager-all.yaml to add the ethernet addresses (the file should look like below)
```
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    ETHER_NAME:
      dhcp4: no
      addresses:
        - YOUR_IP.xx/24
      gateway4: YOUR_IP.xx.1
      nameservers:
        addresses: [8.8.8.8, 8.8.8.4]
```
and apply it.
```
sudo netplan apply
```

It works, but there are two wired networks 'netplan-enpxs0' (default) and 'Wired connection 1' and I don't know why.

---
#### this method also worked at first, but after rebooting the network setting got wrong
2) Open /etc/network/interfaces file by
```
sudo gedit /etc/network/interfaces
```

and add the following:
```
auto ETHER_NAME
iface ETHER_NAME inet static
address YOUR_IP.xx
netmask 255.255.255.0
gateway YOUR_IP.1
dns-nameservers 168.126.63.1 8.8.8.8
```
where ETHER_NAME is the name of the ethernet. It can be checked by the command
`ip a`


then the file looks like:
```
auto lo
iface lo inet loopback


auto ETHER_NAME
iface ETHER_NAME inet static
address YOUR_IP.xx
netmask 255.255.255.0
gateway YOUR_IP.1
dns-nameservers 168.126.63.1 8.8.8.8
```

Finally, save the file and restart the network.
```
sudo /etc/init.d/networking restart
```
---
