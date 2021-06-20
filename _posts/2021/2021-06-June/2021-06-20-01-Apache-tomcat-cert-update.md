---
title: "Jamf Pro On-premises - Apache Tomcat Certificate update"
date: '2021-06-20 16:41:00 +0530'
tags:
  - APPLE
  - JAMF
  - MACADMINS
permalink: "/blog/:title.html"
published: true

---

## At the time of writing this article, I was using :

- macOS Big Sur 11.4 Build 20F71
- Jamf Pro 10.30.0


## Jamf Pro On-premises - Apache Tomcat Certificate update :

*Functionality to issue the Tomcat SSL/TLS certificate from Jamf Pro’s built-in certificate authority — Jamf Pro’s functionality to issue the Tomcat SSL/TLS certificate from the JSS built-in certificate authority (CA) will be discontinued in a future release of Jamf Pro. The release version for this change has not been determined.*

*Before this change occurs, it is recommended that all on-premise Jamf Pro instances leveraging this functionality switch to a publicly trusted third-party CA to issue the Tomcat SSL/TLS certificate. This will prevent the potential loss of MDM communication from Jamf Pro to enrolled devices.*

*If needed, a Tomcat SSL/TLS server certificate for Jamf Pro may be issued from an internal certificate authority. The JSS built-in CA will maintain its current ability to manually issue server certificates to other servers.*

Ref : <https://derflounder.wordpress.com/2021/06/15/jamf-pro-deprecating-the-ability-to-issue-a-tomcat-certificate-from-the-jamf-pro-built-in-certificate-authority/>{:target="_blank"}

1. Generate a 2048-bit private key and a certificate signing request (CSR)

	`openssl req -newkey rsa:2048 -subj "/C=US/ST=MN/L=Minneapolis/CN=Jamf" -keyout ~/Desktop/pavanstaging/privkey.pem -out ~/Desktop/pavanstaging/csr.csr`

	> Tip : When prompted for PEM pass phrase, enter some password. We will need this.

2. Submit the CSR to a certificate authority (CA)

	> 	- Open the CSR file in a text editor and copy the entire content
	> 	- Login to Jamf Pro > Settings > Global Management > PKI Certificates > Management Certificate Template > Create Certifiacte from CSR
	> 	- Certificate Type - Web Server Cert
	> 	- Paste the CSR > Create
	> 	- Downloads the .pem file > Open it > It will be saved in keychain

3. Obtain the CA's public certificate

	> 	- Login to Jamf Pro > Settings > Global Management > PKI Certificates > Management Certificate Template > Download CA Certificate

4. Combine the certificates with the private key in a .p12 file

	`openssl pkcs12 -export -inkey ~/Desktop/pavanstaging/privkey.pem -in ~/Desktop/pavanstaging/csrReplyFromJamfPro.pem -name tomcat -CAfile ~/Desktop/pavanstaging/jamfProBuiltInCA.pem -caname root -chain -passout pass:jamf1234 -out ~/Desktop/pavanstaging/webCertificate.p12`

5. Upload the .p12 file to the Jamf Pro server

	> - Login to Jamf Pro > Settings > System Settings > Apache Tomcat Settings >  Edit > Change the SSL cert used for HTTPS > Upload an existing SSL cert
	> - Upload `~/Desktop/pavanstaging/webCertificate.p12`
	> - Enter the passcode, in this case, it is `jamf1234` (Becasue of the command above)

6. Restart Tomcat	

	```
	sudo /usr/local/jss/bin/jamf-pro server status
	
	sudo /usr/local/jss/bin/jamf-pro server restart
	
	```