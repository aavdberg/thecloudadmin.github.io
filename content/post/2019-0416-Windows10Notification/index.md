---
author: Andre van den Berg
categories:
- Windows 10
- Notification
date: "2019-04-16"
description: How to remove items from the notification list
featured: Windows10Notifications.jpg
featuredalt: Windows10
featuredpath: date
linktitle: ""
tags:
- Windows 10
- Notification
title: Windows 10 App Notifications
type: post
---

## Removing Apps from the notification list in Windows 10 Completely

![Windows10Notification-01](images/Windows10Notification-01.png "Windows10Notification-01")

![Windows10Notification-02](images/Windows10Notification-02.png "Windows10Notification-02")

Some times you want to clean up the apps that are on the notification list. You can empty the list by removing the DB file wpndatabase.db that is located in:

`C:\Users\<user>\AppData\Local\Microsoft\Windows\Notifications`

First, you have to stop the two Windows Push Notifications services like this.

![Windows10Notification-04](images/Windows10Notification-04.png "Windows10Notification-04")

![Windows10Notification-05](images/Windows10Notification-05.png "Windows10Notification-05")

    Get-Service -DisplayName  "Windows Push Notification*" | Stop-Service

Better is to rename the file to wpndatabase.db.original so you can go always back to the previous state.

    Get-Service -DisplayName  "Windows Push Notification*" | Start-Service

When you restart your computer you start with a clean list.

## Only remove one App from the notification list in Windows 10

To remove only one app from the list you have to edit the table HandlerAssets. There is a row with HandlerID that represents a notification item. In the table NotificationHandler, you can find the corresponding number with a description of the program.

With an SQLLite editor, you can view/edit the DB file with the name wpndatabase.db. I used the Navicat for SQLLite.

![Windows10Notification-03](images/Windows10Notification-03.png "Windows10Notification-03")
