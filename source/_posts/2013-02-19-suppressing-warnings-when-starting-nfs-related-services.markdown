---
layout: post
title: "Suppressing warnings when starting NFS-related services"
date: 2013-02-19 20:31
comments: true
categories: [Raspberry Pi]
---

After restarting the Raspberry Pi and the attached paraphernalia every once in a while, the USB HDD that forms the backbone of my NAS needs to be re-mounted each time. The sensible thing to do here would obviously be to manage the re-mounting in a bootup script, but until I get around to doing that I mount the HDD manually.

Since this HDD is used in an NFS share over the network, I also need to export the mount points again and restart the `rpcbind` and `nfs-kernel-server` services. I noticed that every time I did this, the latter service would start up alright, but throw out some odd-looking warnings.

``` console
pi@raspberrypi ~ $ sudo service nfs-kernel-server restart
[ ok ] Stopping NFS kernel daemon: mountd nfsd.
[ ok ] Unexporting directories for NFS kernel daemon....
[ ok ] Exporting directories for NFS kernel daemon....
[....] Starting NFS kernel daemon: nfsdrpc.nfsd: address family inet6 not supported by protocol UDP
 mountdrpc.mountd: svc_tli_create: could not bind to requested address
rpc.mountd: svc_tli_create: could not bind to requested address
rpc.mountd: svc_tli_create: could not bind to requested address
. ok 
pi@raspberrypi ~ $ 
```

The solution to this is quite simple - turns out all you need to do is to edit the file `/etc/netconfig`, which should look something like this:

{% img http://i.imgur.com/Xmx1Ogv.png %}

Just comment out the lines that begin with `udp6` and `tcp` by prefixing each line with a '#', and save the file. (Note that you need to be root or use `sudo` to do this.)

Now when you restart `nfs-kernel-server`, the IPv6-related warnings will be gone!
