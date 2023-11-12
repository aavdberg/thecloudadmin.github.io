---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Configure Routed IPTV on your UBNT EdgeMax or USG"
titlelink: "2020-04-29-XS4All_IPTV_Routed"
subtitle: ""
summary: "XS4All/KPN change from Bridged IPTV to Routed IPTV and will no longer support it. This summer it will stop working also when you read the FOK Forums. Also on the XS4All support website where you find configuration for other modems they only talk about Routed IPTV"
authors: []
tags: [IPTV, XS4All, UBNT, EdgeMax, Internet, Fiber, FttH]
categories: [XS4All]
date: 2020-04-29T09:52:45+02:00
lastmod: 2020-04-29T09:52:45+02:00
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

I never used the FritzBox that XS4All uses at consumers for there Internet/IPTV/VoIP bundle, instead I used the EdgeMax Pro 8 with a EdgeSwitch 16 150W. This worked very well for some years but then I did hear/read on a blog/forum that they switched to Routed IPTV instead of the Bridged IPTV that I still was using.

So did search some on the internet how to reconfigure my EdgeMax Pro 8 to Routed IPTV. Found on the [UBNT forum a threat](https://community.ui.com/questions/USG-Pro-config-for-Netherlands-FTTH-XS4All-Fiber/6e2032cd-2da8-4d10-8984-294a29925a7f) about what people did try to get it working. So spend also a evening trying some configurations.

So I was thinking why not make a blog about it, so I can find it always back and help other people also with it.

## So what is difference between Bridged IPTV and Routed IPTV

With Bridged IPTV you make a bridge group on you router and assign ports to this bridge group, so the SetupBox is directly connected to the IPTV network. With Routed IPTV you route the traffic from your LAN to the IPTV network of your IPTV provider.

So with Bridge IPTV Configuration the Set-Top Box (STB) was connected to the EdgeMax Pro directly, so on eth3 that was a member of the bridge group, and VIF on eth1.4 was also a member of the bridge group.

With Routed IPTV the Set-Top Box (STB) is connected to my EdgeSwitch 16 150W, this makes it also more easy to connect more SetupBoxes in different places in the house.

Why are providers like KPN and XS4All choosing Routed IPTV, this is because to support services like Netflix that use the internet.

## Overview of hardware setup

So I was thinking lets make a drawing how the hardware is set-up.

{{< figure src="images/XS4All_IPTV_Routed-001.png" title="" lightbox="true" >}}

## Step-By-Step Configuration

### Setup routed IPTV

```Powershell
configure

set interfaces ethernet eth1 dhcp-options default-route "no-update"
set interfaces ethernet eth1 dhcp-options default-route-distance 1
set interfaces ethernet eth1 dhcp-options name-server "no-update"

set interfaces ethernet eth1 vif 4 address "dhcp"
set interfaces ethernet eth1 vif 4 description "WAN - IPTV"
set interfaces ethernet eth1 vif 4 dhcp-options client-option "send vendor-class-identifier &quot;IPTV_RG&quot;;"
set interfaces ethernet eth1 vif 4 dhcp-options client-option "request subnet-mask, routers, rfc3442-classless-static-routes;"

set interfaces ethernet eth1 vif 4 dhcp-options default-route "no-update"
set interfaces ethernet eth1 vif 4 dhcp-options default-route-distance "210"
set interfaces ethernet eth1 vif 4 dhcp-options name-server "no-update"
set interfaces ethernet eth1 vif 4 ip source-validation "loose"

commit
save
exit
```

### Modify our DHCP configuration to include IPTV parameters

```Powershell
configure

set service dhcp-server global-parameters "option vendor-class-identifier code 60 = string;"
set service dhcp-server global-parameters "option broadcast-address code 28 = ip-address;"

commit
save
exit
```

### NAT rules are required for the IPTV Set-Top Box (STB) to connect to the IPTV platform

The following commands will return 2 configuration lines required.

```bash
sudo su
r_ip=$(show dhcp client leases | grep router | awk '{ print $3 }');
iptv_static=$(echo "set protocols static route 213.75.112.0/21 next-hop $r_ip")
echo -e "$iptv_static"
exit
```

copy output to text file

```powershell
configure

set service nat rule 5001 description "MASQ corporate_network to IPTV network"
set service nat rule 5001 log disable
set service nat rule 5001 outbound-interface eth1.4
set service nat rule 5001 protocols all
set service nat rule 5001 destination address 213.75.112.0/21
set service nat rule 5001 type masquerade
```

(YOUR SET LINE FOR STATIC ROUTE, received from previous step) Copy the line from the text file and paste it here. 

So will look like understanding:

```powershell
set protocols static route 213.75.112.0/21 next-hop [IP ADDRESS IPTV Router]

commit
save
exit
````

### Setup the IGMP Proxy

```powershell
configure

set protocols igmp-proxy interface eth1.4 alt-subnet 0.0.0.0/0
set protocols igmp-proxy interface eth1.4 role upstream
set protocols igmp-proxy interface eth1.4 threshold 1

set protocols igmp-proxy interface eth7 alt-subnet 0.0.0.0/24
set protocols igmp-proxy interface eth7 role downstream
set protocols igmp-proxy interface eth7 threshold 1

commit
save
exit
```

## Conclusion

I switched my Set-Top Box (STB) off and on, it connected to the IPTV router and downloaded new software and I could look again IPTV on my Set-Top Box (STB).

{{< figure src="images/XS4All_IPTV_Routed-002.jpg" title="" lightbox="true" >}}

## More information and links

Here are some links with more information.

[Netwerkje.com explaining very nicely difference between Bridged vs Routed (Dutch)](https://netwerkje.com/routed-iptv)

[UBTN Forum with thread about configurations for USG also](https://community.ui.com/questions/USG-Pro-config-for-Netherlands-FTTH-XS4All-Fiber/6e2032cd-2da8-4d10-8984-294a29925a7f)

[XS4All Configuration other modems](https://www.xs4all.nl/service/installeren/internet/instellingen-andere-modems/)
