---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "PowerToys Text Extractor"
titlelink: ""
subtitle: "PowerToys Tips"
summary: "Making you life easier with PowerToys Text Extractor"
authors: [André van den Berg]
tags: [PowerToys, Windows, Text Extractor]
categories: [PowerToys]
date: 2023-03-12T11:50:26+01:00
lastmod: 2023-03-12T11:50:26+01:00
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

## PowerToys Text Extraction

I use this daily when i have to extract some text from a image for example to past it in a translation site a Administrator for example installed a server with the France or other language instead of english and then install a language pack over it. Or when i am lazy and don't want to type over the text from a image.

### Good to now about languages other then default on your system

When you want to use the PowerToys Text Extractor tool to extract a other language then your default system language you have to install the OCR language packs.

With the following PowerShell command you can see what OCR language packs are installed. This Powershell command needs to be run with elevated rights.

```powershell
Get-WindowsCapability -Online | Where-Object { ($_.Name -Like 'Language.OCR*') -and ($_.State -Like 'Installed') }
```

and with the PowerShell next command you can see which OCR language packs are available

```powershell
Get-WindowsCapability -Online | Where-Object { ($_.Name -Like 'Language.OCR*') -and ($_.State -Like 'NotPresent') } | Out-GridView
```

and the following PowerShell you can use to install very easy an missing OCR language packs that you selecting

```powershell
$ocrLanguagePacks = Get-WindowsCapability -Online | Where-Object { ($_.Name -Like 'Language.OCR*') -and ($_.State -Like 'NotPresent') } | Out-GridView -OutputMode Multiple -Title 'Select the OCR language packs you want to install'
foreach ($ocrLanguagePack in $ocrLanguagePacks) {
    <# $currentItemName is the current item #>
    $Capability = Get-WindowsCapability -Online | Where-Object { $_.Name -Like $ocrLanguagePack.Name }
    $Capability | Add-WindowsCapability -Online
}
```

{{< figure src="images/PowerToys-Text-Extractor-001.png" title="" lightbox="true" >}}

and off you are to extract text from images other than your default system language.

### How to use

It works the same as the Windows Snipping and Sketch tool, instead of pressing Win + Shift + S you press Win + Shift + T. You then select your

### More information

- [Text Extractor utility](https://learn.microsoft.com/en-us/windows/powertoys/text-extractor)

- [Microsoft PowerToys from the store](https://apps.microsoft.com/store/detail/microsoft-powertoys/XP89DCGQ3K6VLD)

- [PowerToys from GitHub](https://github.com/microsoft/PowerToys)

- [Test Extractor is based on Text Grap](https://github.com/TheJoeFin/Text-Grab)
