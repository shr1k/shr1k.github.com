---
layout: post
title: "Setting up a Raspberry Pi-powered headless media server and NAS"
date: 2013-02-16 09:53
comments: true
categories: [Raspberry Pi]
---

One of the best gifts I've ever received to date is the [End Of The World Survival Kit](http://i.imgur.com/1PSNV.jpg) from my 2012 Reddit Secret Santa. (As an aside, I was so moved by this, that I felt ashamed of taking the easy route of giving my giftee just a T-shirt, and made amends by signing up for re-matching and sending another gift to someone else.)

The best part of the kit was the Raspberry Pi Model B. Recently unemployed and looking for things to do, it was the perfect way to get started on some reasonably techie hobbyism (that's a word now). The only hitch was that I had the board, but no peripherals at all.

Or so I thought.

<!-- more -->

The only items really required to get the RPi up and running are:

- An SD card reader (which my laptop already had)
- A power supply (for which a BlackBerry charger, or any other microUSB charger, will do just fine)  
- An SD card (or microSD card + SD adapter) of 4+ GB  
- An Ethernet cable (hello, dusty old Sky router box! What's this left unused inside you for the last 2.5 years?)

Beyond these, the other required ingredients of this tasty dish are (and some of these may seem obvious):

- A wireless router  
- An externally powered USB HDD of a reasonable capacity (500 GB, in my case)  
- A reasonable number of wireless 'client' devices (laptops, tablets, smartphones) around the house, just to make the effort worthwhile

After this epiphany, getting the whole setup in place was a mere matter of ploughing through the numerous guides published on the interwebs and the odd all-nighter spent figuring out why things didn't work. So here's a quick run-down of the steps involved in -- *drum-roll* -- setting up a Raspberry Pi-powered headless media server and NAS!

1. [Set up the Raspberry Pi](#setup)
2. [Mount external storage](#mount)
3. [Install DLNA server](#server)
4. [Install DLNA client](#client)
5. [Setup NFS](#nfs)

## 1. <a id="setup"></a>Set up the Raspberry Pi

Simply [download](http://www.raspberrypi.org/downloads) the image and ['burn' it onto the SD card](http://elinux.org/RPi_Easy_SD_Card_Setup). I picked Raspbian as I use Ubuntu and am familiar with the Debian way of doing things, and am comfortable with `dd` now (having been burnt a couple of times earlier -- alcohol and `/dev/urandom` do NOT mix well), and opted for the command-line approach.

{% img http://i.imgur.com/anEtp3W.png Preparing the SD card %}

After you plug the prepared SD card into the RPi and power it on, a quick:

`ssh -Y pi@<IP address>` *(using the password "raspberry" without the quotes -- the "-Y" means you can open graphical programs off the RPi on your own screen, but running in the RPi's context)*

and you're logged in. You can find out the IP address of the RPi by checking your router admin page. I'm not sure if there's another way to do this, but this worked for me.

Once logged in, the first thing to do would be to run the **raspi-config** tool (`sudo raspi-config`), "*Expand Root Partition to Fill SD Card*" and reboot (`sudo shutdown -r now` or `sudo reboot`). This ensures you're using the full capacity of the SD card.

{% img http://i.imgur.com/4p63pkN.png Expand Root Partition to Fill SD Card %}

## 2. <a id="mount"></a>Mount external storage

After the OS has been set up, updated and is tootling along happily, plug in the USB HDD. This should be externally powered, because the RPi doesn't appear to be able to power USB devices beyond a keyboard or a mouse.

Keep in mind that the standard Raspbian build does not ship with modern NTFS support, so if you have any partitions formatted as NTFS, you will need to `sudo apt-get install ntfs-3g` to be able to use them properly.

Find the names of the partitions you want to mount (`sudo fdisk -l`), and mount them.

{% img http://i.imgur.com/xzlqnFx.png The required partition names are listed under "Device Boot" %}

I don't mind relying on the smarts of Debian to manage this, so a `sudo mount -t auto /dev/sda1 /media/audvid` should work just fine. Just take care that `/dev/sda1` and `/media/audvid` actually exist first.

## 3. <a id="server"></a>Install DLNA server

The nest step is to install a DLNA/UPnP server. The RPi has MiniDLNA readily available in the repositories, so a `sudo apt-get install minidlna` will suffice.

After it's been downloaded and installed, fire up `/etc/minidlna.conf`, and edit the line that starts with `#media_dir=` to point at your freshly mounted HDD locations. You can use multiple lines for different paths and content types.

{% img http://i.imgur.com/MPV0sxk.png Editing minidlna.conf %}

The other values can be left untouched (unless you want to fiddle about, of course).

Follow this up with a `sudo service minidlna force-reload` to start indexing the new locations. You can follow the progress of this indexing either by tailing the log file with a `tail -f /var/log/minidlna.log` or pointing your browser at `http://<IP address of RPi>:<Port number from minidlna.conf>`.

{% img http://i.imgur.com/6ZJddG9.png MiniDLNA indexing progress %}

This could take a while for large media collections, but one way to guess that indexing has completed is if the log file shows a "Parsing playlists..." message.

Note here that any changes made to these 'watched' locations will necessitate a `sudo service minidlna force-reload`, if the notification options in `/etc/minidlna.conf` haven't been configured.

## 4. <a id="client"></a>Install DLNA client

So you have a DLNA server, but how do you use it? [With a DLNA client, of course](http://en.wikipedia.org/wiki/List_of_UPnP_AV_media_servers_and_clients)! After twiddling with a few options, I settled on the combination of [BubbleUPnP](https://play.google.com/store/apps/details?id=com.bubblesoft.android.bubbleupnp) and VLC, which appears to offer the best balance of free and feature-filled amongst the Android clients. All the rest seemed deficient in one way or another.

{% img left http://i.imgur.com/BL0hrya.png 294 490 BubbleUPnP: Select media source %}
{% img right http://i.imgur.com/xHuvrQ2.png 294 490 BubbleUPnP: Playing audio %}
{% img http://i.imgur.com/v1iTxdL.png BubbleUPnP: Delegating video to VLC %}

## 5. <a id="nfs"></a>Setup NFS

Now what if you need to modify or add to your media library? Futzing around with media metadata and hauling giant files back and forth via DLNA is not possible, and would be too cumbersome over a phone or tablet's interface anyway. Additionally, there doesn't seem to be any sane method of DLNA playback through the Ubuntu desktop.

The best thing to do in this situation remained to mount the media partitions on the USB HDD as network shares. After some consideration of the Samba and NFS approaches, [I decided to go for the latter](https://help.ubuntu.com/8.04/serverguide/network-file-system.html).

Install the NFS server-side components on the RPi using `sudo apt-get install nfs-kernel-server`, which should also install a package called `rpcbind`. After this, add the HDD's mounted partitions into the `/etc/exports` file, save it, and run `exportfs -av`. Follow this up by restarting the `nfs-kernel-server` and `rpcbind` services.

On the client side, do a `sudo apt-get install nfs-common`, and finally, mount the 'exported' paths by saying `sudo mount <IP address>:/media/audvid /home/shrik/Music` and the like. If all succeeds, when you run the `mount` command after this, you should the newly mounted paths at the bottom of the output.

{% img http://i.imgur.com/saHUKcn.png NFS shares mounted successfully %}

At this point, you should be able to make changes in these directories from the client machine, and have these reflected in the RPi.

And there you have it -- a Raspberry Pi running without any I/O peripherals and powering a networked home media centre! I'm not entirely certain how robust this setup will be, but it's been running on a couple of days up-time without any adverse effects so far.

