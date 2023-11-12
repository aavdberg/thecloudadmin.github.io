---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Logon to your Windows 10 device with Azure AD and Security Key"
titlelink: ""
subtitle: ""
summary: "In this blog I will show how you can use a Security Key from for example Yubico or eWBM to logon to your device with an Azure AD account."
authors: []
tags: [Security Key, eWBM, Windows Hello, Passwordless]
categories: [Windows 10]
date: 2020-05-05T16:39:16+02:00
lastmod: 2020-05-05T16:39:16+02:00
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
# {{< figure src="images/WindowsHelloSecurityKey-001.png" title="" lightbox="true" >}}
#
---

## Intro

In this blog I will show how you can use a Security Key from for example Yubico or eWBM to logon to your device with an Azure AD account.

## How to configure it

Go to the following URL: [https://myprofile.microsoft.com](https://myprofile.microsoft.com) you will get something like the following screen.

{{< figure src="images/WindowsHelloSecurityKey-001.png" title="" lightbox="true" >}}

In the MyProfile portal you can do the following things:

* Password, here you can change your password.
* Devices, view, and manage your devices connected to your account.
* My sign-ins (preview), see when you or someone else did try to sign in with your account, it's still in preview but very interesting to see that people use your e-mail address to try to hack your account.
* Organizations, see all the organizations that you're a part of, so all the azure tenants that you have a guest account in.
* Privacy, will show you how the privacy settings are configured in your organization.
* Subscriptions, will show you witch licenses you have assigned to your account.
* Security info, manage like security key's, MFA, Phone numbers, Authentication App. Alternate e-mail, App Passwords.

So we will go to the Security Info tile to configure there our Security Key from eWBM with a fingerprint.

{{< figure src="images/WindowsHelloSecurityKey-002.png" title="" lightbox="true" >}}

Now you see that I already have many different sign-in methods have configured, like my mobile number, office number, App Password, Microsoft Authenticator App, a Security Key from yubico and an alternative e-mail address outside of the tenant.

{{< figure src="images/WindowsHelloSecurityKey-003.png" title="" lightbox="true" >}}

We will click on the 'Add method' to add our eWBM security key with a fingerprint.

{{< figure src="images/WindowsHelloSecurityKey-004.png" title="" lightbox="true" >}}

and select from the method list 'Security key'

{{< figure src="images/WindowsHelloSecurityKey-005.png" title="" lightbox="true" >}}

then you can choose between a USB or NFC device for example, the Yubico has NFC in his device but no fingerprint yet like the eBWM. So we did choose the USB device option.

{{< figure src="images/WindowsHelloSecurityKey-006.png" title="" lightbox="true" >}}

Now you have to insert the USB Security key in de USB port when we click next.

{{< figure src="images/WindowsHelloSecurityKey-007.png" title="" lightbox="true" >}}

{{< figure src="images/WindowsHelloSecurityKey-011.png" title="" lightbox="true" >}}

You see here two screens the first one in black will normally stand over the white one, so we click 'OK'

{{< figure src="images/WindowsHelloSecurityKey-008.png" title="" lightbox="true" >}}

you have now to agree that Microsoft will save your credentials on the security key.

{{< figure src="images/WindowsHelloSecurityKey-009.png" title="" lightbox="true" >}}

you are asked to touch the fingerprint on the security key.

{{< figure src="images/WindowsHelloSecurityKey-010.png" title="" lightbox="true" >}}

When you have touched the fingerprint scanner on the security key the get the option to give the key a name that is easy for you to remember.

{{< figure src="images/WindowsHelloSecurityKey-012.png" title="" lightbox="true" >}}

And now you are ready to use it for logging in on your device with the security key and your fingerprint.

{{< figure src="images/WindowsHelloSecurityKey-013.png" title="" lightbox="true" >}}

When you click on 'Done' your will see that it is added to the overview of your authentication methods, see the understanding screen.

{{< figure src="images/WindowsHelloSecurityKey-014.png" title="" lightbox="true" >}}

## Conclusion

I have a Surface Pro 3 device that has no Windows Hello camera so I use the eWBM Security key with fingerprint daily and are very happy with it, so no Pincode to remember and to type on the keyboard.
