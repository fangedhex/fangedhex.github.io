---
title: Proxmox Setup
date: 2022-08-06 16:19 +0200
categories: [proxmox]
---

# Proxmox Setup

I use ESXi 6.5 on my Dell R620 server but I cannot upgrade it or install vCenter for some reason. Also on ESXi 6.5, I have hard time passing through components.
On Proxmox, it is easier to passthrough with IOMMU and also add software like NUT that I'm going to do later.
I have also multiple disks on it and wanted to manage it as one : there is an hardware raid controller on it but it is very slow and I tried upgrading it and it failed at boot. So I choose to use the software ZFS provided by Proxmox installer (Raid 7 or RaidZ3 in my case because I use old hard drives).

![ZFS Raid levels](/assets/img/raidz.png)

Now that Proxmox is installed and my drives are managed as one, I setup pci passthrough for later. For that, I followed the Proxmox Wiki and added the iommu arguments at the end of the line of /etc/kernel/cmdline like this :

```
root=ZFS=rpool/ROOT/pve-1 boot=zfs quiet intel_iommu=on iommu=pt
```

And then I ran the command to update systemd-boot and rebooted the server :

```bash
proxmox-boot-tool refresh
reboot
```

As tweak I installed both [Nag Buster](https://github.com/foundObjects/pve-nag-buster) and [Dark Theme](https://github.com/Weilbyte/PVEDiscordDark).
Both are simple to do, just run their installer and done.

# Sources

- [Proxmox](https://www.proxmox.com/)
- [PCI Passthrough](https://pve.proxmox.com/wiki/Pci_passthrough)
- [Understanding ZFS Raid levels](http://www.raidz-calculator.com/raidz-types-reference.aspx)
