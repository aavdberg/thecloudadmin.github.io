---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "PowerToys Weekly 17"
titlelink: "2020-PowerToys-Weekly-17"
subtitle: ""
summary: "This is the second week of PowerToys for Windows 10 on our blob, this week we will look at the tool Image Resizer that is part of the PowerToys."
authors: []
tags: [PowerToys, Image, Resizer]
categories: [Windows 10]
date: 2020-04-22T17:48:54+02:00
lastmod: 2020-04-19T17:48:54+02:00
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

This is the second week of PowerToys for Windows 10 on our blob, this week we will look at the tool Image Resizer that is part of the PowerToys.

## Image Resizer what can you do with it

With the Image Resizer you can bulk resize very fast a couple of images that you selected and right click on it and they will be resized but resolution that you selected from the default or the custom size you created your self.

{{< figure src="https://github.com/microsoft/PowerToys/raw/master/doc/images/imageresizer/resizeNormal.gif" title="" lightbox="true" >}}

## Step-by-Step Example

By selecting a couple of images and right click on it and select 'Resize Pictures'

{{< figure src="images/PowerToys-Weekly-ResizeImage-001.png" title="" lightbox="true" >}}

We get the option dialog where we can select the different predefined resolutions and also the option to specify our own custom resolution. Then we can choose some options like do we want to create copies or change the original file. only make pictures smaller and ignore the orientation of the pictures. Also we have an settings option. 

{{< figure src="images/PowerToys-Weekly-ResizeImage-002.png" title="" lightbox="true" >}}

At the Setting -> Sizes tab we can change the predefined sizes but also create a custom new size.

{{< figure src="images/PowerToys-Weekly-ResizeImage-003.png" title="" lightbox="true" >}} 

We can change the encoding at tab encoding

{{< figure src="images/PowerToys-Weekly-ResizeImage-004.png" title="" lightbox="true" >}}

And at the file tab we can define how the file name of the resized file had to look.

{{< figure src="images/PowerToys-Weekly-ResizeImage-005.png" title="" lightbox="true" >}}

Here the original file (left) and the newly (right) created image file.

{{< figure src="images/PowerToys-Weekly-ResizeImage-006.png" title="" lightbox="true" >}}

And your done with a simple couple of clicks.

{{< figure src="images/PowerToys-Weekly-ResizeImage-007.png" title="" lightbox="true" >}}

When you want to know more go to the [GitHub](https://github.com/microsoft/PowerToys/tree/master/src/modules/imageresizer) page of the PowerToys for Windows 10 - Image Resizer.