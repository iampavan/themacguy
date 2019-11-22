---
title: "Force eject external volume"
date: '2019-11-22 19:24:59 +0530'
tags:
  - macOS
  - TROUBLESHOOTING
  - TERMINAL
permalink: "/blog/:title.html"
published: true
---
How to fix: The volume can't be ejected because it's currently in use

## At the time of writing this article, I was using :

- macOS Catalina 10.15.1 Build 19B88

## Steps :

1. Launch the `Terminal.app` from the Utilities folder of your Applications folder

2. Next we need to find the proper name of our disk:
```
ls -ll /Volumes/
```

3. Now let’s find out which system process uses our disk. For this we use the `lsof` tool.
```
sudo lsof | grep /Volumes/Samsung\ T5
```

4. Once we know what process is preventing us from ejecting our disk, we can force it to stop. For this we use the `killall` tool.
```
sudo killall mds
```

5. Sometimes you might need to kill the process by its PID.
```
sudo kill -9 88512
```

6. Testing bash code
{% highlight bash %}
sudo lsof | grep /Volumes/Samsung\ T5
{% endhighlight %}

## Reference articles :

<https://mycyberuniverse.com/macos/how-fix-volume-cant-be-ejected-because-currently-use.html>{:target="_blank"}
