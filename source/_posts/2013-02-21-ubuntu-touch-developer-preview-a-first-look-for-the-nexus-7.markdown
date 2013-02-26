---
layout: post
title: "Ubuntu Touch Developer Preview: A First Look for the Nexus 7"
date: 2013-02-21 20:32
comments: true
categories: [Ubuntu, Ubuntu Touch, Nexus 7]
---

The [Ubuntu Touch Developer Preview](https://wiki.ubuntu.com/Touch/ReleaseNotes) landed today and I was really excited to see it available for my Nexus 7. Following the [really simply install instructions](https://wiki.ubuntu.com/Touch/Install), I was ready to go in less than 30 minutes (and most of that time was just waiting for the OS images to download).

**Quick note**: Please read the [known issues with the Nexus 7](https://wiki.ubuntu.com/Touch/ReleaseNotes#Nexus_7) build before asking questions in [#ubuntu-phone](http://webchat.freenode.net/?channels=ubuntu-phone), as they cover some problems you might notice right away.

<!-- more -->

## Lock-screen and home-screens

The first signs of Ubuntu is the heavily Unity flavoured lock-screen that greets you on booting up. I was a little puzzled by the "14 tweets received" message, but it turns out that it is just a placeholder image.

{% img center http://i.imgur.com/lLoPPkg.png %}

## 
Swiping left or right from the screen edge in the lock-screen takes you to the central home-screen (of five in total). Scrolling and swiping are nice and smooth (with a noticeable stutter when running quite a few apps)

{% img center http://i.imgur.com/vcccQr0.png %}

## 
Swiping left or right in middle of the home-screen navigates between the other home-screens (taking care to stay away from the edges of the screen, as it does something else entirely)

{% img center http://i.imgur.com/Ki8BVvA.png %}

I really hope that the list of "People" that Canonical have set up (all of whom appear to be Canonical employees) have only fake contact details and messaging histories pre-populated in for them, because everyone's phone number is visible, and there's a lot of other potentially personally-identifying information in there.

## 
Swiping left from a home-screen brings up the much maligned Unity launcher.

{% img center http://i.imgur.com/SS2Hx3Q.png %}

## Notification area

There is a notification area on the top right with indicators for messaging, volume control, Wifi, battery status and the time. The notification swipe-down bar is not a unified one a la Android or Symbian^3, but you have to target each tiny icon to bring down its own configuration options. The screenshot below shows the swipe-down options for the time indicator.

{% img center http://i.imgur.com/FA9wY62.png %}

## Apps

The "Apps" home-screen shows the list of "Running", "Frequently Used", "Installed", and "Available for Download" apps in their respective groups.

{% img center http://i.imgur.com/sCcBKOf.png %}

## 
That this is a developer preview is heavily reinforced by the fact that most of the apps are in fact just placeholders and do (nearly) nothing. The calculator and weather apps, for instance, don't do anything at all and are just static images.

{% img left http://i.imgur.com/svmgHqu.png %}
{% img right http://i.imgur.com/hVJLbTb.png %}

## 
There are a few other apps (Amazon, eBay, Gmail) that are essentially the iPhone-optimised versions of the websites wrapped in a browser-frame. The browser appears to be a WebKit container that spits out a Safari 5.1 / iOS user-agent.

{% img center http://i.imgur.com/n4LHcVH.png %}

But it is somewhat functional, and you can navigate to websites by swiping from the bottom screen edge.

{% img center http://i.imgur.com/fGtF8TF.png %}

Some of the (barely) functional native apps are the Notepad and the Photo Gallery. The Notepad loses any created notes on rebooting, but the Photo Gallery is surprisingly functional, with some basic image editing functions like cropping, resizing and enhancing already in place. All these features work quite alright as well.

{% img left http://i.imgur.com/03Y5jjF.png %}

{% img right http://i.imgur.com/k88jZeR.png %}

## 
Swiping up from the bottom screen-edge of every app brings up a set of context-relevant options. Interestingly, a "longer" swipe from the same area brings up a little lens icon, which if targeted, presents a more generic set of actions.

{% img center http://i.imgur.com/QiRIYYj.png %}

There appears to be a bug in its implementation as it stands right now -- I brought this up when in the Calculator app, but it is showing some actions that only apply to photos, like "Share", "Delete", and "Add". However, the "X" icon in the bottom row is the way to exit a running app.

## Keyboard

Oddly enough, the buggiest part of the entire release currently appears to be the keyboard.

{% img center http://i.imgur.com/0TRXCFI.png %}

It is clearly not built for tablets yet, is difficult to use, and generally 'misbehaves' at times. It would keep changing focus to the wrong text-box in the browser, and when I was playing around with the People app, the keyboard decided it never wanted to leave the screen. This was only resolved by a reboot.

**Addendum**: all screenshots were taken with the Nexus 7 connected to the computer and by running `adb shell screencap -p \| uuencode o | uudecode -o <filename>.png`, which saves a PNG screenshot in the current directory.

## Conclusions

I am currently only testing out the release for the Nexus 7, so I'm not in a position to test the camera or the phone-related features like calling or texting. The Nexus 4 is my primary phone, and not really a candidate for experimentation at this stage.

What's next? I guess Canonical will put their nose to the grindstone on this and start churning out functional [core apps](https://wiki.ubuntu.com/Touch/CoreApps). Since this is the first Developer Preview I'm ever playing around with, I couldn't really say if it is a GREAT start, but it certainly sets the stage quite nicely in terms of what to expect. Given that the entire effort essentially appears to amount to [integrating the existing Ubuntu codebase with CyanogenMod](https://wiki.ubuntu.com/Touch/Contribute#Source_code), I'm quite positive that the Canonical team will put out an excellent product.
