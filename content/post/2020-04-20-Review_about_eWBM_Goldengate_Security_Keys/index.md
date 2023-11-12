---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Review about eWBM Goldengate Security Keys"
titlelink: "2020-04-20-Review_about_eWBM_Goldengate_Security_Keys"
subtitle: "Authenticate with FIDO2 keys instead of Passwords"
summary: "Will tell how I did experience the eWBM keys (G320 with USB-C) and (G310 with USB-A) that I did get as Starter Kit from eWBM"
authors: []
tags: [FIDO2, Passswordless, eWBM, Goldengate, Windows Hello]
categories: [Security, Review, Windows 10]
date: 2020-04-20T21:10:17+02:00
lastmod: 2020-04-20T21:10:17+02:00
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

## Intro about FIDO2

FIDO 2.0 (FIDO2) is an open authentication standard that enables people to leverage common devices to authenticate to online services in both mobile and desktop environments. FIDO2 is comprised of the W3C's Web Authentication specification (WebAuthn) and FIDO's corresponding Client-to-Authenticator Protocol (CTAP)

## Why FIDO Authentication

Passwords are the root cause of over 80% of data breaches and users have on average more then 90 account and because of this they reuse password at multiple sites.

{{< figure src="images/eWBM_Review-001.png" title="" lightbox="true" >}}

With FIDO you can use a variety of authentication use cases like Passwordless, Second-factor or Multi-factor.

{{< figure src="images/eWBM_Review-002.png" title="" lightbox="true" >}}

And then people use FIDO in the following ways.

{{< figure src="images/eWBM_Review-003.png" title="" lightbox="true" >}}

# eWBM Starter Kit

As a Microsoft MVP you can get the Starter Kit when you go to the MVP Portal. Myself as a Windows Insider MVP I did not had this option, so send a DM to eWBM and explained. I want to thank eWBM for sending me the two security keys to test.

{{< figure src="images/eWBM_Review-004.jpg" title="" lightbox="true" >}}

## eWBM Goldengate Security key G310

The eWBM Goldengate G310 is a USB-A hardware security key made for FIDO2™️ authentication using eWBM's MS500, a powerful microprocessor with extensive security features and a fingerprint sensor with a world-leading fingerprint recognition algorithm.

When you want to know more about the security key you can go to the site of [eWBM](https://www.ewbm.com/security-keys/goldengate-g310/)

{{< figure src="images/eWBM_Review-005.jpg" title="" lightbox="true" >}}

## eWBM Goldengate Security key G320

This device has the same specifications as de G310 the only difference is that it has USB-C instead of USB-A.

When you want to know more about the security key you can go to the site of [eWBM](https://www.ewbm.com/security-keys/goldengate-g320/)

{{< figure src="images/eWBM_Review-006.jpg" title="" lightbox="true" >}}

## How to set it up

So I used the G310 in my Surface Pro 3 because there is a USB-A port. Then there is a green light on the security key when plugged in the USB port.

In windows 10 I go to the Settings -> Account -> Sign-in options and click on the Security Key.

{{< figure src="images/WindowsPasswordLess-001.png" title="" lightbox="true" >}}

It asks me to touch the security key, so I put my finger on the fingerprint sensor and press Close

{{< figure src="images/WindowsPasswordLess-002.png" title="" lightbox="true" >}}

Now I have to add first a Security Key PIN so I click on the Add button.

{{< figure src="images/WindowsPasswordLess-003.png" title="" lightbox="true" >}}

I type twice the same security key PIN and press on Ok.

{{< figure src="images/WindowsPasswordLess-004.png" title="" lightbox="true" >}}

Yes, now I can setup the Security Key Fingerprint on the Security Key by clicking on the Set up button.

{{< figure src="images/WindowsPasswordLess-005.png" title="" lightbox="true" >}}

For security it ask for the Security key PIN that I set up in the previous steps to verify it's really me.

{{< figure src="images/WindowsPasswordLess-006.png" title="" lightbox="true" >}}

Now I get a screen that is asking to touch the fingerprint sensor repeatedly till the set up is completed. Every time i touch the fingerprint sensor one of the fingerprint lines in the picture changes.

{{< figure src="images/WindowsPasswordLess-007.png" title="" lightbox="true" >}}

Then it says that I am ready and by clicking on Done button the next screen appear.

{{< figure src="images/WindowsPasswordLess-008.png" title="" lightbox="true" >}}

The screen changed at the Security Key Fingerprint, now you have the options add another and Remove.

{{< figure src="images/WindowsPasswordLess-009.png" title="" lightbox="true" >}}

So now I can go to use the Security Key to login to my device or for login to websites.

In a next post I will show how to connect it to your Azure AD account.

## Conclusion

I like the form factor of both Security Key and the fingerprint is a really nice feature because you don't need to type a pin code like you have to do with the YubiKey that now are on the market. What I don't find so practical is that there is no NFC with this keys, on the other hand they don't need batteries.

There is software for the eWBM Security Key G310/G320 to configure the keys, but they where not necessary in this step of setting up the keys for Windows 10.
