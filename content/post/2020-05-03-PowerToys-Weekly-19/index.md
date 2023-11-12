---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "PowerToys Weekly 19"
titlelink: "2020-05-03-PowerToys Weekly 19"
subtitle: ""
summary: "This is the fourth week of PowerToys for Windows 10 on our blog, this week we will look at the File Explorer tool that is part of the PowerToys."
authors: []
tags: [File, Explorer, Windows 10, Preview, Markdown, PowerToys]
categories: [PowerToys]
date: 2020-05-06T18:00:19+02:00
lastmod: 2020-05-04T18:00:19+02:00
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

## Release Info

At the moment that I wrote this blog, the latest version of PowerToys is v0.17.0 and you can find and download the latest version [here](https://github.com/microsoft/PowerToys/releases/tag/v0.17.0).

## Intro

This is the fourth week of PowerToys for Windows 10 on our blog, this week we will look at the tool File Explorer that is part of the PowerToys.

{{< figure src="https://github.com/microsoft/PowerToys/raw/master/doc/images/preview_pane/demo.gif" title="" lightbox="true" >}}

## File Explorer what can you do with it

Everyone knows the File Explorer but with the PowerToys you get some additional functionality with it, in the form of a preview pane for Markdown and SVG files. And when you are a developer you can also make your own preview handlers how they are called. There is also a big amount of information about how to make yourself a preview handler with .NET.

[Information about File Explorer / Development of preview Handler](https://github.com/microsoft/PowerToys/tree/master/src/modules/previewpane)

## Step-By-Step Example

When you open the PowerToys you get the general settings and there you can enable File Explorer.

{{< figure src="images/PowerToys-Weekly-19-001.png" title="" lightbox="true" >}}

When you then click on the left on the File Explorer you can enable Markdown and/or SVG preview.

{{< figure src="images/PowerToys-Weekly-19-002.png" title="" lightbox="true" >}}

And in the future, I think there will come more preview handlers for common file extensions.
