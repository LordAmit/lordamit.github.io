---
layout: post
title: Remix OS Resident Mode in Virtual Machine
date: '2016-03-04 11:17:11 +0600'
description: "It is now possible to setup Remix OS in virtual Machine. Yes, in resident mode, which was not possible earlier. And this article will guide you step by step to achieve just that."
comments: true
modified: '2016-04-19 22:37:00 +0600'
tags: [tutorial, android, Linux]
---
Long story short, it is now possible to run Remix OS in Virtual Machine (or Virtual Box) in resident mode.
{% figure caption:"Remix OS in Virtual Machine" %}
![Remix OS in Virtual Machine](https://farm2.staticflickr.com/1481/25837025506_8cc2d7d6e8_b.jpg)
{% endfigure %}
How?
<!-- more -->

### Install
To prepare the installation environment properly, you need to:

3. Make a virtual machine first - Recommended: 8GB Space, 1GB RAM
2. Use Ubuntu Installer ISO or any other preferred tool to boot it
3. Use GParted or other disk utility tool to format the entire hard disk to EXT4 format
4. Reboot, use the RemixOS installer ISO

During installation - choose the following options:

1. Do not format
1. Install GRUB
1. Do not Install UEFI Grub Thingy
6. Complete Installation

### Tweaks for Resolution (Experimental)
In default mode, the resolution sucks. Of course, we can fix that by assigning the resolution through grub. Note that incorrect DPI and resolution settings can frequently cause force reboot abruptly.

There are two approaches:

- Change the resolution settings EVERY-SINGLE-Time you boot your Remix OS
- Change the resolution settings using an editor in root mode, once and for all.

You will need both approaches. Because finding the perfect resolution takes some experimentation.

### Change Resolution in Runtime
When your Remix OS shows boot menu, press `e`, and then `e` again. See the `VGA=791` part? That is setting your resolution. We are going to `UVESA_MODE` and `DPI` for better resolution. Modify and insert the part instead of `VGA=791`. **Keep everything else the same.** I tested and found the following settings useful:

{% highlight shell %}
DPI=160 UVESA_MODE=1366x768
DPI=265 UVESA_MODE=2880x1800
{% endhighlight %}

*This settings may not work properly for your display device. You need to change the DPI and the resolution according to your display capability. Just remember that higher DPI = bigger, less DPI = Smaller.*

Press `ESC` to discard changes, or Press `Enter` to temporarily save changes.  and press `B` to boot using the temporary settings.

Once you find your perfect resolution head over to next step.

### Change Resolution Permanently
1. Hit up your Ubuntu once again, and mount the EXT4 partition.
2. Open up your terminal. Probably the partition will be mounted in `/media/ubuntu-gnome`. For example, mine was mounted in `/media/ubuntu-gnome/`.
3. Go into the mounted volume, and there you will see 3 folders.
4. Go into the grub folder.
5. Use your favorite editor in root mode to edit the menu.lst file.
6. In the first entry, remove the `VGA=791` and replace it with  `DPI=160 UVESA_MODE=1366x768`.

Save and reboot!
That's all. Enjoy. :)

### Acknowledgements
I took help from the following sites:

1. [Remix OS 2.0 x86/x64 iso : RemixOS](https://www.reddit.com/r/RemixOS/comments/406982/remix_os_20_x86x64_iso/)
2. [Google Groups](https://groups.google.com/forum/#!topic/remix-os-for-pc/NB6GJdAHUsA)_
3. [virtualbox - Switch android x86 screen resolution - Stack Overflow](http://stackoverflow.com/questions/6202342/switch-android-x86-screen-resolution/8273560#8273560)
4. [GRUB VGA Modes](http://pierre.baudu.in/other/grub.vga.modes.html)
