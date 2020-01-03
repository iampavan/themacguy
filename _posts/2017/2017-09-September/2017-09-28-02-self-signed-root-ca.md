---
title: "Deploy Self-signed RootCA to client computers"
date: 2017-09-28 23:55:59 +0530
tags:
  - macOS
  - MAC ADMINISTRATION
  - JAMF
permalink: "/blog/:title.html"
header:
  teaser: "/assets/images/blog-posts-images/06-self-signed-root-ca.png"
comments: true
published: true
---

2 computers required :

1. ServerMac
2. ClientMac


## On ServerMac :

Create a Certificate Authority and export the Root Certificate (If you already have a self-signed RootCA that you want to deploy, then you can skip this part)

1. Open Keychain Access.
2. Select the System keychain.
<br/>
<br/>
![1.png](/assets/images/blog-posts-images/self-signed-root-ca/1.png)
<br/>
3. From the Keychain Access menu, navigate to Certificate Assistant and select Create a Certificate Authority.
<br/>
<br/>
![2.png](/assets/images/blog-posts-images/self-signed-root-ca/2.png)
<br/>
4. For the name, enter “MyCompany Root CA”.
5. Select SSL Server from the User Certificate pop-up menu.
6. Deselect “Make this CA the default.”
7. Enter admin@mycompany.com as the email address.
<br/>
<br/>
![3.png](/assets/images/blog-posts-images/self-signed-root-ca/3.png)
<br/>
8. Click Create, then close the Certificate Assistant.
9. Search for the new root certificate identity called “MyCompany Root CA”.
<br/>
<br/>
![4.png](/assets/images/blog-posts-images/self-signed-root-ca/4.png)
<br/>
10. Double-click the “MyCompany Root CA” certificate.
<br/>
<br/>
![5.png](/assets/images/blog-posts-images/self-signed-root-ca/5.png)
<br/>
11. Click the Trust disclosure triangle.
12. From the “When using this certificate” pop-up menu, select Always Trust.
<br/>
<br/>
![6.png](/assets/images/blog-posts-images/self-signed-root-ca/6.png)
<br/>
13. Close the “MyCompany Root CA” certificate inspection window.
14. When prompted, enter the admin credentials for your ServerMac and click Update Settings.
15. Select all three “MyCompany Root CA” keychain items and drag them to the System keychain.
16. When prompted, enter the admin credentials for your ServerMac and click Modify Keychain.
17. Click Always Allow.
18. Select the “MyCompany Root CA” certificate, then choose Export Items from the File Menu.
<br/>
<br/>
![7.png](/assets/images/blog-posts-images/self-signed-root-ca/7.png)
<br/>
19. Save the certificate on your Desktop folder.



Create certificate for the intranet website (This is not required; just to verify later we will create this).

1. Open Server and select Certificates from the Server group on the left.
2. Click the Add (+) button and choose “Create a Certificate Identity” from the pop-up menu.
3. In Certificate Assistant, enter “intranet.mycompany.com” as the name.
4. For Identity Type, choose Leaf.
5. Click Create.
6. When prompted to choose an issuer, select “MyCompany Root CA” and click Create.
7. Click Done.If prompted, enter the admin credentials for your server and click OK.
8. When prompted to add the certificate to the system keychain, click Always Allow.A new certificate appears in the list of certificates for your server.

OR

You can also create a leaf certificate with this method : (this is done without the Server app)

1. Keychain Access > Certificate Assistant > Create a certificate
2. Name – Intranet ; Identity Type – Leaf ; Certificate Type – SSL Client
3. Sign it with your earlier created “MyCompany Root CA”
<br/>
<br/>
![8.png](/assets/images/blog-posts-images/self-signed-root-ca/8.png)
<br/>
<br/>
![9.png](/assets/images/blog-posts-images/self-signed-root-ca/9.png)
<br/>
<br/>
![10.png](/assets/images/blog-posts-images/self-signed-root-ca/10.png)
<br/>
<br/>
![11.png](/assets/images/blog-posts-images/self-signed-root-ca/11.png)
<br/>

***

# Next, we need to create a Configuration Profile. There are couple of ways to do this:

> Method 1 : We can directly upload the RootCA.cer in the JSS. The advantage of this method is, the Client devices will not be able to delete the profile from the System Preference. The “minus” symbol will be greyed out for them.


Go to your JSS

1. Configuration Profile > New
2. Give a Name ; Distribution Method > Install Automatically; Level > Computer level
3. Certificate > Configure ; upload the “RootCA .cer” file; Save
4. Scope > whatever
<br/>
<br/>
![12.png](/assets/images/blog-posts-images/self-signed-root-ca/12.png)
<br/>
<br/>
![13.png](/assets/images/blog-posts-images/self-signed-root-ca/13.png)
<br/>
<br/>
![14.png](/assets/images/blog-posts-images/self-signed-root-ca/14.png)
<br/>
<br/>
![15.png](/assets/images/blog-posts-images/self-signed-root-ca/15.png)
<br/>
<br/>
![16.png](/assets/images/blog-posts-images/self-signed-root-ca/16.png)
<br/>



## On ClientMac :

1. The Profile pane now lists the “MyCompany” cert profile. (Cannot be removed by user)
<br/>
<br/>
![17.png](/assets/images/blog-posts-images/self-signed-root-ca/17.png)
<br/>
2. You can also verify in Keychain app. It will be in System keychain.
<br/>
<br/>
![18.png](/assets/images/blog-posts-images/self-signed-root-ca/18.png)
<br/>
<br/>
<br/>
![19.png](/assets/images/blog-posts-images/self-signed-root-ca/19.png)
<br/>
3. If the endusers are using any service which is signed with RootCA like the eg. “intranet” leaf certificate. You can see that it says “Valid”.
<br/>
<br/>
![20.png](/assets/images/blog-posts-images/self-signed-root-ca/20.png)
<br/>

***

> Method 2 : We can create .mobileconfig profile which contains that RootCA certificate in it, then upload it to JSS

1. There are many ways, here I am using Apple Configurator 2 to create .mobileconfig file
2. Open AC2, File > New Profile
3. Certificates > Configure > “Add that certificate”
4. Save
5. Go to your JSS
	1. Configuration Profile > Upload
	2. Distribution Method > Install Automatically
	3. Level > Computer level
	4. Scope > whatever
<br/>
<br/>
![21.png](/assets/images/blog-posts-images/self-signed-root-ca/21.png)
<br/>
<br/>
![22.png](/assets/images/blog-posts-images/self-signed-root-ca/22.png)
<br/>
<br/>
![23.png](/assets/images/blog-posts-images/self-signed-root-ca/23.png)
<br/>
<br/>
![24.png](/assets/images/blog-posts-images/self-signed-root-ca/24.png)
<br/>
<br/>
![25.png](/assets/images/blog-posts-images/self-signed-root-ca/25.png)
<br/>
<br/>
![26.png](/assets/images/blog-posts-images/self-signed-root-ca/26.png)
<br/>
<br/>
![27.png](/assets/images/blog-posts-images/self-signed-root-ca/27.png)
<br/>
<br/>
![28.png](/assets/images/blog-posts-images/self-signed-root-ca/28.png)
<br/>
<br/>
![29.png](/assets/images/blog-posts-images/self-signed-root-ca/29.png)
<br/>
<br/>
![30.png](/assets/images/blog-posts-images/self-signed-root-ca/30.png)
<br/>
<br/>
![31.png](/assets/images/blog-posts-images/self-signed-root-ca/31.png)
<br/>
<br/>
![32.png](/assets/images/blog-posts-images/self-signed-root-ca/32.png)
<br/>
<br/>
![33.png](/assets/images/blog-posts-images/self-signed-root-ca/33.png)
<br/>
<br/>
![34.png](/assets/images/blog-posts-images/self-signed-root-ca/34.png)
<br/>
<br/>
![35.png](/assets/images/blog-posts-images/self-signed-root-ca/35.png)
<br/>
<br/>
![36.png](/assets/images/blog-posts-images/self-signed-root-ca/36.png)
<br/>


## On ClientMac :

1. The Profile pane now lists the “MyCompany” cert profile. (Can be removed by user)
2. You can also verify in Keychain app. It will be in System keychain.
<br/>
<br/>
![37.png](/assets/images/blog-posts-images/self-signed-root-ca/37.png)
<br/>
<br/>
![38.png](/assets/images/blog-posts-images/self-signed-root-ca/38.png)
<br/>
<br/>
![39.png](/assets/images/blog-posts-images/self-signed-root-ca/39.png)
<br/>
<br/>
![40.png](/assets/images/blog-posts-images/self-signed-root-ca/40.png)
<br/>
<br/>
![41.png](/assets/images/blog-posts-images/self-signed-root-ca/41.png)
<br/>
