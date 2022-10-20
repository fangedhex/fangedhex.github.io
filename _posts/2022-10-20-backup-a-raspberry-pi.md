---
layout: post
title: Backup a raspberry pi
date: 2022-10-20 16:57 +0200
categories: [raspberrypi,backup]
---

I wanted to backup my current raspberry pi sd card so I can install something else on it. And if it doesn't work, I can come back to that backup.
The thing is that if I back it up, the image will be the size of the sdcard so I need to shring it. Here is how I proceeded (it was very simple).

To create my image file, I used [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/) to do just that. 

![Win32 Disk Imager Main Window](/assets/img/win32diskimager.png)

1. Put the path where to save the image
2. Select the sdcard device
3. Click on read and wait until it finish.

After that I used [PiShrink](https://github.com/Drewsif/PiShrink) on my Ubuntu WSL (Windows Subsystem for Linux) to shrink it to the smallest size possible. Just type that in a linux console :

```bash
pishrink -Zap {filename}
```

My sdcard was shrinked from 64 GiB (full size) to 1 GiB
