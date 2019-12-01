---
title: "Jamf on AWS"
date: '2019-10-25 23:24:59 +0530'
tags:
  - DOCKER
  - JAMF PRO
  - JSS
  - AWS
  -
permalink: "/blog/:title.html"
header:
  teaser: "/assets/images/blog-posts-images/jss-on-aws/jamf-aws.png"
published: true
---

## At the time of writing this article, I was using :

- Jamf Pro 10.16
- macOS Catalina 10.15.0 Build 19A602


# What are we setting up...

1. Jamf on Docker Containers
- This will run locally on the machine
- <https://bryson3gps.wordpress.com/2019/11/25/so-you-want-to-containerize-jamf-pro/>{:target="_blank"}

2. Jamf on AWS
- Makes use of above docker.
- Google domain needed to add CNAME.
- <https://bryson3gps.wordpress.com/2019/11/25/so-you-want-to-run-serverless-jamf-pro/#comment-4733>{:target="_blank"}

3a. Azure LDAP and Azure SSO

- <https://hcsonline.com/images/PDFs/Jamf_Microsoft_Azure_Integration.pdf>{:target="_blank"}
- <https://hcsonline.com/images/Identity_Management_Azure_Jamf.pdf>{:target="_blank"}

- Used some of these mappings : <https://travellingtechguy.eu/integrate-azure-ldap-in-jamf-pro/>{:target="_blank"}

3b. JumpCloud as LDAP provider and SSO.

- <https://travellingtechguy.eu/jumpcloud-as-ldap-provider-in-jamfcloud-jamfpro/>{:target="_blank"}




## Prerequisites for the setup :

1. Amazon AWS account - <https://aws.amazon.com/free/>{:target="_blank"}
2. Jamf Pro Manual Installer
	- Login to your jamfnation account <https://www.jamf.com/jamf-nation/>{:target="_blank"}
    - Click Account > My Assets

    ![1.png](/assets/images/blog-posts-images/jss-on-aws/1.png)

    - Jamf Pro Manual Installation > Download

    ![2.png](/assets/images/blog-posts-images/jss-on-aws/2.png)


## Reference articles :

1. @rtrouton - [Creating a Jamf Pro Cloud Distribution Point using Amazon Web Services](https://derflounder.wordpress.com/2017/03/07/creating-a-jamf-pro-cloud-distribution-point-using-amazon-web-services/){:target="_blank"}

2. @Richard Purves - [JSS and AWS: Cloud Design for a beginner](https://www.richard-purves.com/2017/03/09/jss-and-aws-cloud-design-for-a-beginner/){:target="_blank"}
