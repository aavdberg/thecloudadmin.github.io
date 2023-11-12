---
author: Andre van den Berg
categories:
- Hugo
- DevOps
date: "2018-12-08"
description: Explained how to enable submodules for your Hugo themes in Azure DevOps.
featured: helloazuredevops.png
featuredalt: helloazuredevops
featuredpath: date
linktitle: ""
tags:
- tutorial
title: Submodules in your DevOps CI/CD for Hugo
type: post
---

## Submodules in your DevOps CI/CD for Hugo

When you are building your site with the Hugo website generator you can load the themes as a Submodule in your repository with the following command:

```Git
git submodule add https://github.com/jpescador/hugo-future-imperfect.git themes/hugo-future-imperfect
```

But when you then commit and push your changes to your Git repository in Azure DevOps and run the following command:

```Bash
Hugo -v
```

In your build pipeline and then go to your website you will see that the theme is missing from your site

To solve this problem change the following setting (marked yellow) in your Build Pipeline.

![Submodules in DevOps](images/submodulesindevopsforhugo.png "Submodules in DevOps")
