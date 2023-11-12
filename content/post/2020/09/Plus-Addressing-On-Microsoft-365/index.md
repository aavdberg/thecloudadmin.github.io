---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Plus Addressing on Microsoft 365"
titlelink: ""
subtitle: ""
summary: "Plus Addressing is a great way to quickly create custom (or disposable) email addresses based off your standard email address, by simply adding a '+' suffix string to an existing email address in Office 365"
authors: []
tags: [Exchange Online, Mail, Plus Addressing]
categories: [Microsoft 365]
date: 2020-09-24T14:34:28+02:00
lastmod: 2020-09-24T14:34:28+02:00
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

### Intro

How many times you want to download some software and have to give you email address before you can download it. now you can create in a fast way a special e-mail address for this.

So for example your e-mail address is: info@thecloudadmin.eu and don't want to use this for the download form where you have to fill in your address.

So you will fill in info+download@thecloudadmin.eu

What wil happen is that the mail is delivered to your info@thecloudadmin.eu, but now you can easily filter on this mails. And move them to a special folder, or even delete the mails right away.

### Activate Plus Addressing on your Microsoft 365 tenant

You can only activate it tenant wide. 

You first have to have the Exchange PowerShell module installed, the following [article](https://docs.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps) will help you with this.

Then you can use the following PowerShell command to activate it on your tenant.

```powershell
Set-OrganizationConfig -AllowPlusAddressInRecipients $true
```

### How to filter on Plus Addressing

You can filter on the to: address. it will look like info+download@thecloudadmin.eu

### Conclusion

I think this is a very handy solution when you give someone a e-mail where you can filter very easy on.


