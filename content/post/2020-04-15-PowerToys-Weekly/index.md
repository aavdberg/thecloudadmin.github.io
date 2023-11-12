---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "PowerToys Weekly 16"
titlelink: "2020-PowerToys-Weekly-16"
subtitle: ""
summary: "Weekly we will look at one of the tools in PowerToys"
authors: []
tags: [PowerToys]
categories: [Windows 10]
date: 2020-04-15T18:33:40+02:00
lastmod: 2020-04-15T18:33:40+02:00
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
---

## Intro to the PowerToys for Windows 10

Who worked with Windows 95 and XP probably heard of the PowerToys there where included 15 tools for Power Users.

And now the PowerToys are back for Windows 10 and as opensource to be found on [GitHub](https://github.com/microsoft/PowerToys)

## PowerToys Weekly

The idea is to take every week one of the tools and explain what they do precisely. So this week we will start with the PowerRename tool that is available in the PowerToys for Windows 10.

## PowerRename what can you do with it

With PowerRename you can fast and easy rename a bulk of files.

{{< figure src="https://github.com/microsoft/PowerToys/raw/master/src/modules/powerrename/images/PowerRenameDemo.gif" title="" lightbox="true" >}}

## Step-by-Step Example

We select a selection of files or Folder where files reside inside that we want to manipulate and then right click on the selected files or folder and choose PowerRename like on the understanding picture.

In our example we select a couple of images.

{{< figure src="images/PowerToys-Weekly-PowerRename-001.png" title="" lightbox="true" >}}

Then we right click on the selection.

{{< figure src="images/PowerToys-Weekly-PowerRename-002.png" title="" lightbox="true" >}}

We get the PowerRename tools with all the options that we can use the manipulate our selected images.

{{< figure src="images/PowerToys-Weekly-PowerRename-003.png" title="" lightbox="true" >}}

Then we say that we want to search with a regular expressions by putting at Options a checkmark at (Use Regular Expressions).

At the 'Search for' field we fill in .* so we select all the files. In the 'Replace with' field we fill in the new name we want to give the files. And we want a counting up number appended to the file name so we put at options a checkmark at (Enumerate Items).

In the preview window we will see the result and can click op Rename when we are happy with the preview and then the files be be renamed.

{{< figure src="images/PowerToys-Weekly-PowerRename-004.png" title="" lightbox="true" >}}

Here you see the result went the PowerRename tool is completed.

{{< figure src="images/PowerToys-Weekly-PowerRename-005.png" title="" lightbox="true" >}}
