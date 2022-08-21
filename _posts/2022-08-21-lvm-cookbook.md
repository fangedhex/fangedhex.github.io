---
layout: post
title: LVM Cookbook
date: 2022-08-21 10:43 +0200
categories: [linux,lvm]
---

# Physical Volume (PV) Management

```bash
# Create a PV
pvcreate {partition}
```

{partition}
: /dev/sda1 for example

```bash
# View current PVs
pvdisplay
```

# Volume Group (VG) Management

```bash
# Create a VG
vgcreate {vg_name} {partition}
```

{vg_name}
: Name of the VG you want to create

{partition}
: Partition to add the VG

```bash
# Extend a VG with a new PV
vgextend {vg_name} {partition}
```

{vg_name}
: Name of the VG you want to create

{partition}
: Partition to add the VG

```bash
# View current VGs
vgdisplay
```

# Logical Volume (LV) Management

```bash
# Create a LV
lvcreate -L {size} {vg_name} -n {lv_name}
```

{size}
: Size of the new Logical Volume
> Can be written in G, M, K or 100%FREE

{vg_name}
: Volume Group in which we create the Logical Volume

{lv_name}
: Name for the created Logical Volume

```bash
# View current LVs
lvdisplay
```

## Concatenation

```bash
# Resize LV to get the space remaining (sinc we extended the VG)
lvresize -l +100%free {lv_path}
```

{lv_path}
: Logical Volume path
> can be found with ```lvdisplay | grep Path```

Don't forget to resize your filesystem (ext4, btrfs ...)

## Mirror

```bash
# Setup LV for Raid1
lvconvert --type raid1 --mirrors 1 {lv_path}
```

{lv_path}
: Logical Volume path
> can be found with ```lvdisplay | grep Path```

