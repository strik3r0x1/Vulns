# ========== Stored-XSS at ZTC GK420d printer ==========
##### Discoverer: (Eslam Kamal (Strik3r))[https://www.linkedin.com/in/eslam-kamal/]
##### Vendor of Product: Zebra Technologies
##### Affected Product: ZTC GK420d

## Description
Stored Cross-Site Scripting (XSS) vulnerability has been identified in the web portal of ZTC GK420d printers, manufactured by Zebra Technologies. By injecting malicious JavaScript code into the web interface, attackers can manipulate the printer's functionality, compromise sensitive data, or launch further attacks against connected devices or networks. This could include actions such as redirecting users to malicious websites, stealing session cookies, or capturing login credentials entered into the compromised portal.


## POC
Steps To Reproduce:
1. Navigate to any of vulnerable hosts at /settings and enter login password
2. Navigate to “Alert Setup” endpoint

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/49069606-d653-4017-a2dc-d5d512a442f6)

3. Click on “add alert message”
4. At the address field ad any value with XSS payload and enter password again

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/1991bc0c-6805-42f5-91c5-69733120aaea)

5.	After click on “add alert message” you will notice this confirm that our payload saved.

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/66b7c375-217c-4bb5-9bce-41272ee91a4c)

6.	Now click on alert setup button to return to this endpoint again and notice our payload pop-up

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/b2a5a99c-2951-4d37-bd8e-773278460f8f)











