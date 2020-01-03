---
title: "Imaging will be gone (soon-ish)"
date: 2017-03-05 23:55:59 +0530
tags:
  - macOS
  - MAC ADMINISTRATION
  - APPLE FILE SYSTEM
permalink: "/blog/:title.html"
comments: true
published: true
---

I don’t normally try to foretell the future but there is one change for Mac admins that I’m pretty sure will happen:

The coming of Apple File System (APFS) will mark the end of disk imaging on Macs.

For those not familiar with disk imaging, a disk image is a computer file containing the contents and structure of a disk volume. Mac disk images are applied to hard drives using the Apple Software Restore (asr) command line utility to erase the destination drive and then block-copy the data from the disk image onto the destination drive.

Mac deployment practices have generally fallen into one of three categories:

## Monolithic imaging

Monolithic imaging is the practice of building a Mac with the desired operating system, desired software, and desired configuration settings, then creating a disk image which includes all the contents of that Mac’s boot drive, including the operating system, installed software, and settings.

Once that disk image is created, the image is then applied to multiple other Macs to make them just like the original Mac.

## Modular imaging

Modular imaging is the practice of creating a disk image that contains only the base OS (as well as necessary OS updates from Apple).

Once that disk image is created, the image is applied to multiple other Macs. Desired software and desired configuration settings are then installed onto the newly-imaged Mac as post-imaging deployment tasks.

## Thin imaging

Thin imaging is technically not an imaging practice, as no disk image is involved. Instead, the assumption is that Macs from Apple come with a pre-installed OS and that OS should be used instead of wiping it and replacing it with a new copy from a disk image.

In this scenario, a deployment workflow is run which installs the desired software and desired configuration settings onto the Mac. If a Mac needs to be wiped and re-setup, a fresh copy of the OS is installed via the Recovery environment or similar OS installation process and then the thin imaging deployment workflow is re-run.

Imaging using asr has been around for a long time (I first began using it back in the Mac OS X 10.2.x days) but there have been strong hints that those days are coming to an end. The most visible of these was this tweet from the makers of DeployStudio:

> @ygini I bet that system imaging will end with APFS. You should focus on DEP, MDM and loosely coupled directory integration.
>
> — Deploy Studio (@deploystudio) January 8, 2017

While the makers of DeployStudio don’t speak for Apple, a statement like this matches up with what I’ve heard from other Mac admins who have independently received similar messages as part of their communication with Apple. Apple hasn’t commented publicly one way or the other, so unfortunately I can’t be more specific than that.

If imaging isn’t available, what are the alternatives? Apple has been encouraging the use of Apple’s Device Enrollment Program, which leverages a company, school or institutions’ mobile device management (MDM) service. In this case, you would need to arrange with Apple or an Apple reseller to purchase Macs that are enrolled in your organization’s DEP.

When a DEP-enrolled Mac is started for the first time (or started after an OS reinstall), it is automatically configured to use your organizations’ MDM service and the device checks in with the MDM service. The MDM service then configures the Mac as desired with your organization’s software and configuration settings. A good example of what this process may look like can be seen here.

What if you don’t have DEP, or you don’t have MDM? In that case, you may still be able to leverage a thin imaging deployment workflow, which installs the desired software and desired configuration settings onto the Mac’s existing OS. To get an existing OS though, you would need to install it via the Recovery environment or a similar OS installation process.

## Planning for the future

Today, imaging works and our deployment workflows are what they are. What should be done to prepare for the future?

If you’re already using DEP with MDM to set up your Macs:

> Congratulations! You’re good to go with a Apple-supported deployment workflow that should work fine for the foreseeable future.

If you’re not using DEP with MDM to set up your Macs:

> If DEP is an option for your organization and you have an existing MDM service, investigate using Apple’s DEP service to set up your Macs for deployment. You may find that DEP doesn’t work for you in its current form, but now is the time to find that out and work with Apple to get those parts fixed.
>
> If DEP isn’t an option for your organization (because you aren’t using MDM and/or you aren’t in a country where DEP is supported) and you aren’t using a thin imaging deployment workflow now, I recommend investing the time and effort to start using a thin imaging workflow. In particular, if you are using monolithic imaging to set up your Macs, it is time to stop and transition to an alternate way of deploying Macs before that imaging method abruptly stops working.

When will we know how long imaging has left? My recommendation will be to watch what Apple reveals at this summer’s WWDC 2017 conference and pay particular attention to any device management or APFS developments that are being announced, as those announcements should likely provide the best information.`

When in doubt, visit [isimagingdead.com][web-page-1]{:target="_blank"}


## Reference articles :

- <https://derflounder.wordpress.com/2017/01/10/imaging-will-be-dead-soon-ish/>{:target="_blank"}


[web-page-1]: http://isimagingdead.com/
