---
title: "Creating PAYLOAD-FREE Package"
date: 2017-09-18 23:55:59 +0530
tags:
  - macOS
  - TERMINAL
  - PACKAGING
  - MAC ADMINISTRATION
permalink: "/blog/:title.html"
comments: true
published: true
---


## Creating PAYLOAD-FREE Package


Here’s how we make a “true” payload-free package (that does not leave a receipt):

```
pkgbuild --nopayload --scripts /path/to/scripts_dir --identifier org.example.payloadfree --version 1.0 MyGreatPayloadFree.pkg
```

But payload-free packages built this way have a “feature” that can sometimes prove problematic. Flat packages built with `pkgbuild` using the `--nopayload` option do not leave receipts in the `pkgutil` database. This means it can be difficult to determine if a given payload-free package has already been installed on a given machine.

This is especially annoying with Munki: by default, when installing a package, Munki uses the package’s receipt(s) to determine whether or not the package has been installed. Without that receipt, and with no other information, Munki can’t tell if the package has been installed.

Fortunately, it’s trivial to make a pseudo-payload-free package that leaves a receipt. All we need to do is specify an empty payload!

<br/>

***

<br/>

and here’s a “pseudo” payload-free package that does leave a receipt:

```
mkdir empty
pkgbuild --root empty --scripts /path/to/scripts_dir --identifier org.example.payloadfree --version 1.0 MyGreatPayloadFree.pkg

```

That’s it! Instead of using the `--nopayload` option, we create an empty directory and point the `--root` option at it. The package is built with the empty payload, and when installed, the package leaves a receipt.

<br/>

## Reference articles :

- <https://managingosx.wordpress.com/2010/02/18/payload-free-package-template/>{:target="_blank"}
- <https://derflounder.wordpress.com/2014/06/01/understanding-payload-free-packages/>{:target="_blank"}
- <https://managingosx.wordpress.com/2015/05/20/pseudo-payload-free-pkgs-with-pkgbuild/>{:target="_blank"}
- <https://derflounder.wordpress.com/2015/05/21/payload-free-package-creator-app-revisited/>{:target="_blank"}
- To learn more about packages : <https://www.youtube.com/watch?v=oKxjxi9Eny8>{:target="_blank"}
