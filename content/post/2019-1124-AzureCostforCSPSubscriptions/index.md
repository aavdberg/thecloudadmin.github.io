---
author: Andre van den Berg
categories:
- Azure
- Cost
date: "2019-11-24"
description: Now you can see Azure Cost with a CSP Subscription like you already could with Pay-As-You-Go subscriptions.
featured: azure-costs.jpg
featuredalt: Azure-Cost
featuredpath: date
linktitle: ""
tags:
- Azure
- Cost
title: Azure Cost and CSP (Cloud Solution Partners) Subscriptions working
type: post
profile: false
---

For this functionality I was waiting already for over a year and also many other people with me and Last week they announced it was GA. The only thing your CSP has to do is change your agreement to the new Microsoft Customer agreement.

When you look at the overview of your subscription it's very important that at Plan is standing 'Azure Plan' else it won't work.

{{< figure src="images/AzureCSPCost.000.jpg" title="" lightbox="true" >}}

You have to give the user account or group that you are using to login to the azure portal  the 'Billing Reader' role if you don't already have this role assigned to your user account or group.

{{< figure src="images/AzureCSPCost.002.jpg" title="" lightbox="true" >}}

And when your CSP have done al the required steps you should get the understanding screen, and you can do the same things I described in my other [blog][1] some months ago.

{{< figure src="images/AzureCSPCost.001.jpg" title="" lightbox="true" >}}

And the you want to know more about this subject you can go to the [following link][2] at the Microsoft blog announcements.

[1]: https://www.thecloudadmin.eu/blog/2019-0205-azurecostmanagement/
[2]: https://azure.microsoft.com/nl-nl/blog/introducing-azure-cost-management-for-partners/
