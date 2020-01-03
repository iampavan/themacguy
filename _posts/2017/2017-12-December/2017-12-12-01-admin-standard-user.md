---
title: "Admin user in GUI, but Standard user in CLI"
date: 2017-12-01 23:55:59 +0530
tags:
  - macOS
  - SERVER
  - MAC ADMINISTRATION
permalink: "/blog/:title.html"
comments: true
published: true
---

> Q : Does the latest version of OS X Server have print server capabilities? If I have three printers that are AirPrint compatible and would like to check whether there’s a way to pre-install drivers on a configuration file for a user to plug in to his or her Mac and all the printers be configured automatically.


So, the answer to this is no. But a more round-about answer is sort of (as far as driver delivery and config), depending on your infrastructure.

Ok, base answer. There is no “print server” in OS X Server any more.  Instead, you can add printers to the server and share them using system preferences.  But if they are network printers (or AirPrint printers) they are already broadcasting on the network so resharing them will only result in multiple broadcast queues.  Likewise, OS X and Server alone can not “deliver” print drivers to devices.

Now, there are products that can accomplish this. For example, you can look at something as simple as Apple Remote Desktop. Now, the process would still be manual in that you would have to push the drivers to the device and you would have to have credentials for the device. So if these are not devices owned by you that is likely not going to work.  If you have a fleet of devices, JAMF is a great solution as all software can be delivered dynamically and transparently to the end user.  But, that is really for environments over 50 devices.

But, all that said, if you have a device that is not configured to the printer and you select the printer, is the device able to find the driver in Apple’s software repository? For small deployments where you may not control the individual systems, that is likely the easiest way.

Or, you can place the drivers and a configuration script on a file share.


## Reference articles :

- <https://discussions.apple.com/thread/7038478?start=0&tstart=0>{:target="_blank"}
