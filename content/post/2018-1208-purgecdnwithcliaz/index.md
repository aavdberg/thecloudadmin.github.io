---
author: Andre van den Berg
categories:
- Hugo
- DevOps
- Azure
- CLI
date: "2018-12-08"
description: Explained how to purge your CDN content with Azure CLI in Azure DevOps.
featured: msdeveloper.png
featuredalt: msdeveloper
featuredpath: date
linktitle: ""
tags:
- tutorial
title: Purge CDN content with Azure CLI in your DevOps CI/CD for Hugo
type: post
---

## Purge CDN content with Azure CLI in your DevOps CI/CD for Hugo

After your Azure DevOps CI/CD Pipeline has finished you want that you Azure CDN content get purged so your blog visitors will see the latest content and changes you have made to your blog.

I was searching on the internet with my best friend google and post how you can do this with PowerShell but then I was thinking why not using Azure CLI with AZ.

So found that you can use the following command:

```CLI
az cdn endpoint purge -g $ResourceGroupName -n $EndpointName --profile-name $ProfileName --content-paths '/*'
```

So tested this in the Azure Cloud Shell to look if this worked, and after some time the command was finished. So I looked in the log in the Azure portal and did see the following:

![Activity Log CDN](images/purgecdnwithaz1.png "Activity Log CDN")

Then i added a new task in the Release Pipeline of my DevOps project for Hugo to purge the CDN endpoint for my blog site.

![Added Task to Release Pipeline](images/purgecdnwithaz.png "Added Task to Release Pipeline")

And added the variables for ResourceGroup, ProfileName, and EndPointName in the Release Pipeline.

![Added Task to Release Pipeline](images/purgecdnwithaz2.png "Added Task to Release Pipeline")
