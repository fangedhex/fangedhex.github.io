---
layout: post
title: Debian Network configuration
date: 2022-08-17 16:45 +0200
---

# Configure a static IP

We need to modify the network configuration file /etc/network/interfaces to add this :

```
auto ens18
iface ens18 inet static
  address 192.168.0.2
  netmask 255.255.255.0
  gateway 192.168.0.1
```

# Configure custom dns servers

We need to modify the network configuration file /etc/resolv.conf to add this :

```
nameserver dns1
nameserver dns2
nameserver dns3
```
