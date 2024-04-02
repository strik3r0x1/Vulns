
### ===== CSRF at Clavister E80,E10 lead to Reset/Reboot Firewall =====
##### Discoverer: [Eslam Kamal (Strik3r)](https://www.linkedin.com/in/eslam-kamal/)
##### Vendor of Product: Clavister
##### Affected Product: Clavister E80,E10 - EagleSeries
-----------------------------------
![image](https://github.com/strik3r0x1/Vulns/assets/94288990/75b04a25-2610-4e48-b1d8-af95c4253d25)

## Overview
Cross-Site Request Forgery (CSRF) is an attack that forces an end user to execute unwanted actions on a web application in which they’re currently authenticated. With a little help of social engineering (such as sending a link via email or chat), an attacker may trick the users of a web application into executing actions of the attacker’s choosing. If the victim is a normal user, a successful CSRF attack can force the user to perform state changing requests like transferring funds, changing their email address, and so forth. If the victim is an administrative account, CSRF can compromise the entire web application.

## Description
The CSRF vulnerability detected in the Clavister E80 and E10 firewall systems allows attackers to forge requests on behalf of authenticated users, leading to unintended actions such as rebooting or resetting the firewall. By crafting a malicious link or embedding it within a legitimate website, attackers can deceive users into unknowingly executing unauthorized actions, ultimately compromising the security and integrity of the network.
A successful attack could result in Unauthorized firewall reboots or resets, leading to disruption of network traffic and services


## POC
This vulnerability was discovered in the (Clavister E10 and E80 ) Firewall at Reset endpoint **"/?Page=Reset"**

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/710a9322-7da1-4289-b70b-96378b103779)

As example we created a form to simulate a typical HTTP request for the **/?restart=full&Page=ResetAction** endpoint in order to use it in our proof of concept.

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/73948b13-498f-4d61-8b8d-4927ab6ef2dc)

Because the application does not validate the request, if any authenticated user clicks on that button, the application accepts the request and the user cookies are sent through the request to the **"/htdocs/pages/base/sys reset.lsp"** endpoint, causing the Firewall to reboot.

The same method will be used in order to create a CSRF POC in order to Reset all Firewall configurations at **/?reset=factoryreset&Page=ResetAction** endpoint.

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/6319e2c3-94be-422b-8234-53c26844df36)











