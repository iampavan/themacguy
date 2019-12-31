---
title: "How to create a blog (Like this one.. Literally!)"
date: '2019-08-25 23:24:59 +0530'
tags:
  - Jekyll
  - Blog
  - Website
  - Github
permalink: "/blog/:title.html"
header:
  teaser: "/assets/images/blog-posts-images/02-blog.png"
published: true
---
Step by step guide to build a Jekyll site

## At the time of writing this article, I was using :

- macOS Mojave 10.14.6
- Ruby vXXX



## Reference articles :

- <https://jekyllrb.com/docs/installation/macos/>{:target="_blank"}
- <https://medium.com/@hisa_py/jekyll-with-asdf-ruby-fix-ruby-ffi-loaderror-on-macos-high-sierra-c302f0567e9b>{:target="_blank"}
- <https://botsplash.com/blog/migrating-from-medium-to-jekyll-and-netlify-cms.html>{:target="_blank"}
- <https://mmistakes.github.io/minimal-mistakes/docs/configuration/>{:target="_blank"}
- <https://dev.to/trentyang/how-to-setup-google-domain-for-github-pages-1p58>{:target="_blank"}
- <https://help.github.com/en/articles/troubleshooting-custom-domains>{:target="_blank"}
- <https://jekyllrb.com/docs/configuration/options/>{:target="_blank"}

- <https://didecentral.com/contributors-guide/site-config/#changing-the-font-size>{:target="_blank"}


Hotjar website tracking
- <https://mycyberuniverse.com/add-hotjar-tracking-to-jekyll-website.html>{:target="_blank"}


Jekyll theme
- <https://rubygems.org/search?utf8=%E2%9C%93&query=jekyll-theme>{:target="_blank"}


Adding Dark mode (auto) :
- <https://derekkedziora.com/blog/dark-mode-revisited>{:target="_blank"}
- Tip : I also cloned Derek's repo and played around running locally on my machine <https://github.com/derekkedziora/derekkedziora.com>{:target="_blank"}
- <https://derekkedziora.com/blog/dark-mode>{:target="_blank"}
- <https://talk.jekyllrb.com/t/night-mode-plugin/428>{:target="_blank"}


Adding Search bar :
- <https://medium.com/@urre/instant-jekyll-search-f77065d60047>{:target="_blank"}
- <https://blog.webjeda.com/instant-jekyll-search/>{:target="_blank"}


Adding comments section :
- <https://help.disqus.com/en/articles/1717111-what-s-a-shortname>{:target="_blank"}
- <https://darekkay.com/blog/static-site-comments/>{:target="_blank"}
- <https://mademistakes.com/articles/jekyll-static-comments/>{:target="_blank"}


Adding favicon :
- <https://medium.com/@xiang_zhou/how-to-add-a-favicon-to-your-jekyll-site-2ac2179cc2ed>{:target="_blank"}


Adding Webpage icon for iOS home screen :
- Need to edit `_includes/layout/head.html` file.
- <https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html>{:target="_blank"}
- <https://github.com/philipithomas/jekyll-resume/blob/master/_includes/layout/head.html>{:target="_blank"}


Random
- <https://www.youtube.com/watch?v=NoRS2D-cyko&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=11>{:target="_blank"}

- <https://joshua-d-miller.com/new-theme-for-blog/>{:target="_blank"}
- <https://github.com/artemsheludko/flexible-jekyll>{:target="_blank"}




## To-do items :

1. Dark mode needs to be refined.

2. Few posts are not horizontal-wrapping. Eg. <http://127.0.0.1:9111/blog/01-Build-Jekyll-site.html>{:target="_blank"}
When viewed from an iOS device, it should nicely wrap. Eg. <https://themacguy.in/blog/02-volume-not-ejecting.html>{:target="_blank"}
