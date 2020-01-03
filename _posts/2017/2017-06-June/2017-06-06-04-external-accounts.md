---
title: "External accounts behaviour"
date: 2017-06-06 23:55:59 +0530
tags:
  - macOS
  - SERVER
  - ATSP
  - TRAINING
permalink: "/blog/:title.html"
comments: true
published: true
---

## At the time of writing this article, I was using :

- macOS Sierra 10.12.x

## Here’s the configuration :

* A Mac with 2 partitions – “Sierra 1” and “Sierra 2”.
* We try to demo Manual enrollment on Partition 1 and Automated enrollment on Partition 2.
* So, there is a “User 01” mobile account on Partition 2.
* Now, when I boot the Mac into Partition 1, I get this pop-up window at its login window. Why?

![1.jpg](/assets/images/blog-posts-images/2017/external-accounts/1.jpg)

## My take :

macOS has a feature to allow you to store your mobile or managed account on a separate or external HardDisk and use this User to login to various Macs. You can basically carry your user account with you – physically. Or you just relocate your Users to another partition. Some Customer like to use this for Administration and/or Support Capabilities.
You should be able to avoid this Pop-Up by disabling external accounts via a config profile during enrolment. This can be found in the Loginwindow Payload.


![2.png](/assets/images/blog-posts-images/2017/external-accounts/2.png)


The feature itself has been around for a long time, at least 10.6., maybe 10.5.
The option to control the behaviour trough a mobileconfig is much newer, though.
At least in my personal experience, the external accounts feature is really seldom used and quite many might suggest avoiding it.
Of course, this is just my opinion and there might be customers using it, loving it and relying on it.
