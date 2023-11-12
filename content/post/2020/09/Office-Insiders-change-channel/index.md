---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Switch between channels (Office Insider) with Microsoft 365 Apps for Business or Enterprise"
titlelink: ""
subtitle: "The easy way to switch between channels with Microsoft 365 Apps for Business or Enterprise"
summary: "How to switch between channels with Microsoft 365 App for Business/Enterprise without re-installing with custom Install with a XML file."
authors: []
tags: [Office 365, Microsoft 365, Office]
categories: [Office Insiders]
date: 2020-09-06T13:59:27+02:00
lastmod: 2020-09-06T13:59:27+02:00
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

With Microsoft 365 Home for example you can switch between channels (Office Insider), by going to File -> Accounts and there you have on the right the following button:

{{< figure src="images/Office-Insiders-change-channel-001.png" title="" lightbox="true" >}}

When you click on it you get the following options

{{< figure src="images/Office-Insiders-change-channel-002.png" title="" lightbox="true" >}}

By clicking on "Change Channel" you get a screen where you can join and change from channel

{{< figure src="images/Office-Insiders-change-channel-003.png" title="" lightbox="true" >}}


But wait you would say, with the Microsoft 365 Apps for Business or Enterprise I don't have the

{{< figure src="images/Office-Insiders-change-channel-001.png" title="" lightbox="true" >}}

Button at all. Your right, by default this button is not there for Microsoft 365 Apps for Business or Enterprise.

So what i did in the past de-install my Office Insider and configure and install it with the [Custom Install](https://insider.office.com/en-us/business/deploy/windows/office-deployment-tool)

### Getting the Change Channel Button for Office Insider

By configuring a GPO or adding a Registry Key you can make appear the following button

{{< figure src="images/Office-Insiders-change-channel-001.png" title="" lightbox="true" >}}

Configuring it with a GPO looks like the following:

{{< figure src="images/Office-Insiders-change-channel-004.png" title="" lightbox="true" >}}


> When enabling this policy, make sure the Update Channel and Update Path policies aren’t enabled or the Office Insider button will show but the selected Insider settings will not apply.

Configuring it with a registry key looks like this:

{{< figure src="images/Office-Insiders-change-channel-005.png" title="" lightbox="true" >}}

You could use the following PowerShell command to create it:

{{< figure src="images/Office-Insiders-change-channel-006.png" title="" lightbox="true" >}}

```powershell
New-Item -Path HKCU:\SOFTWARE\Policies\Microsoft\Office\16.0\common\ -force | New-ItemProperty -Name insiderslabbehavior -PropertyType DWORD -Value 1 -Force
```
After you close and open an Microsoft 365 App you will see the Office Insiders button.

### Switching between channel builds

You can also use the following registry 

```powershell
New-Item -Path HKCU:\SOFTWARE\Policies\Microsoft\Office\16.0\common\officeupdate -force | New-ItemProperty -Name updatebranch -PropertyType REG_SZ -Value "InsiderFast" -Force
```
There following name you can place on the above line as value, to get the different Office channels.

* InsiderFast
* FirstReleaseCurrent 
* Current
* MonthlyEnterprise 
* FirstReleaseDeferred 
* Deferred

When you did the change you have to choose File --> Account and the Update Option

{{< figure src="images/Office-Insiders-change-channel-007.png" title="" lightbox="true" >}}

and then Update Now

{{< figure src="images/Office-Insiders-change-channel-008.png" title="" lightbox="true" >}}

And the you will have a other office channel build without re-installing.

### Conclusion

This trick saved me many time and now can also switch fast between channel versions when I have to test something. The blog from [MSOutlook.info](https://www.msoutlook.info/question/office-365-for-business-office-insider-fast-builds) helped my to get this done.

