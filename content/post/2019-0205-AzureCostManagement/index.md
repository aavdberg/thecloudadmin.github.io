---
author: Andre van den Berg
categories:
- Azure
- Cost
date: "2019-02-06"
description: Using Cost Management in Azure to control costs with budgets
featured: azure-costs.jpg
featuredalt: Azure-Cost
featuredpath: date
linktitle: ""
tags:
- Azure
- Cost
title: Azure - Cost control with budgets
type: post
profile: false
---

### In this blog I will show how to configure budgets in Azure Cost Management + Billing

When I was looking at the cost center last day I see that there was changed something. You can now define budgets in the blade Cost Management.

The following screen is an example of creating a budget with alerts and the amount that the budget is. You can configure a start and end date and the period after it resets the budget.

{{< figure src="images/AzureBudget.001.jpg" title="" lightbox="true" >}}

You can also create action groups that you can use every time not to repeat you them in your budget and where you can group actions.

{{< figure src="images/AzureBudget.002.jpg" title="" lightbox="true" >}}

here an example of an action group where you can group together actions.

{{< figure src="images/AzureBudget.003.jpg" title="" lightbox="true" >}}

With an action you have the following options: Email so you can send an e-mail then there is an alert, but also an SMS but beware of the fact that you can have cost with this for sending SMS messages. You can also do a push through you azure app on your phone.

{{< figure src="images/AzureBudget.004.jpg" title="" lightbox="true" >}}

Here an example of a complete configured budget with action group, so Reset is set to Monthly and the amount to 100 with an end date far in the future, the nice thing is that you now can see how many you already spend and how many you already used of your total budget.

{{< figure src="images/AzureBudget.005.jpg" title="" lightbox="true" >}}

The cost analysis page looks also very nice where you get an overview of your subscription.

{{< figure src="images/AzureBudget.006.jpg" title="" lightbox="true" >}}
