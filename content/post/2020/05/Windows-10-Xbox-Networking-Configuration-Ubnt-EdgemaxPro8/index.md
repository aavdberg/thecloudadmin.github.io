---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Windows 10 Xbox Networking configuration for UBNT EdgeMax Pro 8 router"
titlelink: ""
subtitle: ""
summary: "When testing Windows 10 as Windows 10 insider MVP i was seeing that i did get errors at Xbox Networking at Gaming section in the Settings menu. So did some research on the internet and configured the UBNT EdgeMax Pro 8 router that i am using for my Internet connection to XS4All Fiber to the Home (FFTH) connection."
authors: []
tags: [EdgeMax Pro, UBNT, XBox, PS4, Router, Internet, Windows Defender]
categories: [Windows 10]
date: 2020-05-29T21:41:33+02:00
lastmod: 2020-05-29T21:41:33+02:00
featured: false
draft: false
profile: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []

# Example of posting a picture with shortcode
#
# {{< figure src="images/BackgroundEffectTeams-007.png" title="" lightbox="true" >}}
#
---

## Intro

When testing Windows 10 as Windows 10 insider MVP I was seeing that i did get errors at Xbox Networking at Gaming section in the Settings menu. So did some research on the internet and configured the UBNT EdgeMax Pro 8 router that i am using for my Internet connection to XS4All Fiber to the Home (FFTH) connection.

So in the following screenshot you see how it has to be when everything is configured the right way in your UBNT EdgeMax Pro 8 Router.

{{< figure src="images/XBox-Networking-Configuration-EdgemaxPro8-001.png" title="" lightbox="true" >}}

When you get also a error then probaly UPnP or UPnP2 is not enabled on your router.

## Why enabling UPnP matters

UPnP stands for “Universal Plug and Play” and allows an application to automatically forward a port on your router or gateway, saving you the hassle of forwarding ports manually. There has been much debate about UPnP being a security risk as any application on your network can open ports to the outside world and some people refer to UPnP as a system for “dumb people, incapable of configuring port forwarding rules”.

If you do not use Skype or play games on PS4, Xbox or Steam there should really be no reason to use UPnP if you are paranoid. UPnP avoids the hassle of manually configuring port-forward rules and keeping track of which ports should be forwarded can become quite a challenge. There are many console games which will actually only properly work with UPnP enabled (especially if you have multiple consoles on the same network).

The real security challenge with UPnP is that if a virus, trojan, worm or other malicious program gets on your network which then will be capable of opening ports to the outside world, bypassing your firewall entirely. As an example, a Trojan horse could install a remote control program on your computer and open a port for it in your router’s firewall, allowing 24/7 access to your computer from the Internet. If UPnP was disabled, the program could not open that port, but might be able to bypass the firewall in other ways and phone home.

Since UPnP assumes that local programs are trustworthy (such as your PS4 or games running on it, or Skype), it allows them to forward ports. It is really up to the user to ensure that malicious programs do not run on the home-network (use malware scanners and antivirus software and do not download pirated software).

## What to Configure in your UBNT EdgeMax Pro 8 Router.

You go to the web interface of your UBNT EdgeMax Pro 8 Router, then in the right corner you have the following:

{{< figure src="images/XBox-Networking-Configuration-EdgemaxPro8-002.png" title="" lightbox="true" >}}

Here you click on the CLI and this will open a Terminal where you first have to login with the username and password that you also used to login to the website.

{{< figure src="images/XBox-Networking-Configuration-EdgemaxPro8-003.png" title="" lightbox="true" >}}

When you are logged-in you will get the following:

{{< figure src="images/XBox-Networking-Configuration-EdgemaxPro8-004.png" title="" lightbox="true" >}}

Now you have to bring the router in configuration mode, you can do this with the following command:

```markdown
configure
```

now there will show the following in the terminal

```markdown
ubnt@milkyway:$ configure
[edit]
ubnt@milkyway#
```

Now you have to configure the following settings in the terminal on your UBNT EdgeMax Pro 8:

here you setup that UPnP2 is listening on eth1 in our case the LAN interface, so you have to replace eth1 with the port witch your LAN is connected to.

```markdown
set service upnp2 listen-on eth1
```

Now you enable for upnp2  the network address translation (NAT) - Port Mapping Protocol (PMP)

```markdown
set service upnp2 nat-pmp enable
```

Here you will configure the more secure kind of UPnP namely UPnP2.

```markdown
set service upnp2 secure-mode enable
```

Here we configure that the WAN interface is eth0, so you have to configure where you WAN interface is connected to.

```markdown
set service upnp2 wan eth0
```

Now remove the old UPnP version 1 from the router, to make it a little bit more secure.

```markdown
delete service upnp
```

after this you have to do the following commands:

```markdown
commit
save
exit
```

And your terminal will be closed and your Xbox and also your Windows 10 PC will be able to use the Xbox Networking.

## Conclusion

So you can do two things to get it working enabling UPnP2 on your UBNT EdgeMax Pro 8 Router, or leave it disabled and going the difficult route and configure forwarding your self on the router, with the same risk because then you PC or XBox or PS4 get hacked your network is still breached.

So my advise is to always leave the Windows firewall enabled on your Windows 10 devices and not like many people do is disabling it because they think i am behind and firewall and in my LAN is everything safe.

And keep your Windows Defender always up-to-date and also with the latest definitions updates that microsoft releases several times a day.

And wish you happy gaming on your Windows 10 device or your Xbox device.
