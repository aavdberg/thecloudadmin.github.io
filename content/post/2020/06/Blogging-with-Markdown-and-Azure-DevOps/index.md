---
title: Blogging With Markdown and Azure DevOps
titlelink: ''
subtitle: ''
summary: 'I wanted to go blogging, but not with WordPress because i don''t like PHP language so much. And i wanted to learn more about Azure DevOps and did see that Jekyl was not so active as Hugo. So decided to write my blog with Markdown and use Hugo to generate the site content. And could learn at the same time Azure DevOps by putting the source in Azure DevOps Repo and use Build pipeline for automatically generating content and use Release pipeline to put the generated content on an Azure Web App'
authors: []
tags:
  - Blogging
  - Markdown
  - Hugo
  - Azure
  - DevOps
  - CD/CI
  - Pipelines
categories:
  - Azure
  - DevOps
date: 2020-05-30T12:09:57.000Z
lastmod: 2020-05-30T12:09:57.000Z
featured: false
draft: true
profile: false
image:
  caption: ''
  focal_point: ''
  preview_only: false
projects: []
---

## Intro

"I wanted to go blogging, but not with WordPress because i don't like PHP language so much. And i wanted to learn more about Azure DevOps and did see that Jekyl was not so active as Hugo. So decided to write my blog with Markdown and use Hugo to generate the site content. 

And could learn at the same time Azure DevOps by putting the source in Azure DevOps Repo and use Build pipeline for automatically generating content and use Release pipeline to put the generated content on an Azure Web App"

## Creating an new Project in Azure DevOps

So with that in mind I started a new project in Azure DevOps.

#### Step 1: Login to Azure DevOps

Login to https://dev.azure.com or Create a new DevOps environment

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-001.png" title="" lightbox="true" >}}

#### Step 2: Create a new Organization or New project

Create a new Project.

When you create a new project in your existing organization, you can go to the right upper conner and select 'New project'

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-002.png" title="" lightbox="true" >}}

Else when you login for first time in Azure DevOps it will ask you to create a new project.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-003.png" title="" lightbox="true" >}}

So we will make a new project with the name 'FamBerg-Hugo' and make it a private project, this means only the people that you give permissions can read or write to it or both, depends on what permissions you give.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-004.png" title="" lightbox="true" >}}

Now we have a empty project with nothing in it.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-005.png" title="" lightbox="true" >}}

#### Step 3: Create a Repo

So we go to create a new Repo by clicking on the 'Repos' icon in the left menu. 

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-006.png" title="" lightbox="true" >}}

You will get the following screen to because the repo is not initialized yet.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-007.png" title="" lightbox="true" >}}

We click on the 'Initialize' button to let Azure DevOps do this for us.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-008.png" title="" lightbox="true" >}}

Now we have a initialized repo in Azure DevOps.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-009.png" title="" lightbox="true" >}}

#### Step 4: Install the Required software

But first we need to install all the required software and tools on our machine.

I am using now the days only Windows Terminal for my command-line tools and shells like Command Prompt, PowerShell, PowerShell Preview, Windows Subsystem for Linux (WSL). 

So the following software I am using in this blog:

* Windows Terminal
* Git
* VSCode
* Hugo Site Generator

But now we will be using PowerShell and Git. So when you don't have [Windows Terminal](https://docs.microsoft.com/en-us/windows/terminal/) you can download it from the [Windows Store](https://www.microsoft.com/store/productId/9N0DX20HK701). And Git you can download from [here](https://git-scm.com/download/win) for the Windows version. Visual Studio Code you can download from [here](https://code.visualstudio.com/#alt-downloads) And as last Hugo Site Generator you can download from [Here](https://github.com/gohugoio/hugo/releases) But when you are lazy like me you can download and install it with the following command:

But a requirement is that you have installed Windows Package Manager that you can download from [here](https://github.com/microsoft/winget-cli/releases)

```powershell-interactive
winget install --id=Git.Git -e && winget install --id=Microsoft.VisualStudioCode -e && winget install --id=Microsoft.WindowsTerminal -e
```

Hugo is still not available on WinGet so you can install it manual or with chocolaty with the following command:

```powershell-interactive
choco install hugo-extended -confirm
```

#### Step 5: Clone DevOps Repo to Local devices

So now we go to clone the DevOps repository local to the machine that you are working on.

So start the Windows Terminal and go to the path where you want the local git repository stored.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-010.png" title="" lightbox="true" >}}

Use the following command to clone you repository you created at Step 3.

```markdown
git clone https://FamBerg-Demo@dev.azure.com/FamBerg-Demo/FamBerg-Hugo-Demo/_git/FamBerg-Hugo-Demo
```
 
You will get now a prompt for authentication to you repository in Azure DevOps.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-011.png" title="" lightbox="true" >}}

After you authenticated the clone will be made.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-012.png" title="" lightbox="true" >}}


#### Step 6: Create a new Blog site wih Hugo

Now you have a empty git repository with only a README.md in it. 

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-013.png" title="" lightbox="true" >}}

So we go to create a blank Hugo Site with the following command.

```markdown
Hugo new site .\ --force
```

This will create the new site directly in the current directory therefore we are using the ---force flag.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-014.png" title="" lightbox="true" >}}

When we look now in the current directory we see that there are some folders are created.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-015.png" title="" lightbox="true" >}}

And also the git part of the command line changed from green to yellow because there where changes in the local repository.

Now we have to have a theme so we going to use the Ananke theme and add it with the following command:

```markdown
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
```

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-016.png" title="" lightbox="true" >}}


Now we run the following command to test the new website:

```markdown
hugo server
```

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-017.png" title="" lightbox="true" >}}

In the Edge browser we can now use:

```markdown
http://localhost:50273/
```

And get the following.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-018.png" title="" lightbox="true" >}}

#### Step 6: Setting up App Service Plan

Now we have local our blog site running but off course we want to run it in Azure.

When you now yet used Azure you can watch [this Video on youtube](https://www.youtube.com/watch?v=oMNfDAm9FVs) by Dane Epp

First we have to login to the [Azure Portal](https://portal.azure.com)

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-019.png" title="" lightbox="true" >}}

We are going to create a resource group in Azure where we can deploy all our resources in that are related to or blog site.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-020.png" title="" lightbox="true" >}}

We give our resource group a name and choose the region we want it deployed in.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-021.png" title="" lightbox="true" >}}

We will click on the create button and this will create the resource group where we can put all the resources related to our blog site.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-022.png" title="" lightbox="true" >}}

Now we have a empty resource group. 

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-023.png" title="" lightbox="true" >}}

Click on the Add button

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-024.png" title="" lightbox="true" >}}

And type in the search field 'App Service Plan'

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-025.png" title="" lightbox="true" >}}

Click on the create button to create the App Service Plan.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-026.png" title="" lightbox="true" >}}

At the name field give it a meaningful name and choose the region where you want the app service plan deployed.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-027.png" title="" lightbox="true" >}}

Then choose the right Sku and size you want to use, i will use in this case the tree tier. So click on the change size text that is printed in blue.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-028.png" title="" lightbox="true" >}}

I choose for this demo for the Dev / Test and then the F1 that is free. When selected click on Apply.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-029.png" title="" lightbox="true" >}}

So now we can click on the Review + Create button to create the App Service Plan.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-030.png" title="" lightbox="true" >}}

And then we click on create when everything looks good.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-031.png" title="" lightbox="true" >}}

The App Service Plan will be deployed and after some minutes it will be ready.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-032.png" title="" lightbox="true" >}}

Now we can click on the resource group: FamBerg-Site-Demo

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-033.png" title="" lightbox="true" >}}

As you see we have now a resource item that we just created in our resource group.

Now we are going to create the Web Service so we create on Add again while standing in our resource group.

{{< figure src="images/Blogging-with-Markdown-and-Azure-DevOps-034.png" title="" lightbox="true" >}}

In the search field we type Web App and press on enter.
