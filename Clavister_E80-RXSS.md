# == Reflected-XSS chained with CSRF at Clavister E80 Firewall ==
##### Discoverer: [Eslam Kamal (Strik3r)](https://www.linkedin.com/in/eslam-kamal/)
##### Vendor of Product: Clavister
##### Affected Product: Clavister E80 - EagleSeries
-----------------------------------
![image](https://github.com/strik3r0x1/Vulns/assets/94288990/338e9f93-aff1-426f-818e-f9c7bd32e394)

## Description
Reflected XSS chained with CSRF poses a threat to Clavister E80 Firewall-protected web applications. In this scenario, attackers inject malicious scripts into the application, which execute in users' browsers, potentially leading to unauthorized actions like data theft or manipulation. While the firewall provides network security, it may not safeguard against these specific web application vulnerabilities. Mitigation strategies include secure coding practices, such as input validation and output encoding, as well as implementing anti-CSRF tokens and conducting regular security assessments.


## POC
This vulnerability was discovered in the Misc. Settings **"/?Page=Node&OBJ=/System/AdvancedSettings/DeviceSettings/MiscSettings"** endpoint at 8 parameters.

Steps To Reproduce:

1. When trying to add any JavaScript code inside any input field, the Firewall will refuse it due to the validation of the values characters on the fron-end.

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/25b7510e-7301-4c75-852e-c93b1a999ce8)

So, to trigger cross-site script code as shown below, we intercepted the Misc Settings Configuration HTTP POST request and changed the values of 8 parameters:
"WatchdogTimerTime","BufFloodRebootTime","MaxPipeUsers","AVCache Lifetime","HTTPipeliningMaxReq","Reassembly MaxConnections","Reassembly MaxProcessingMem" and "ScrSaveTime".

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/25ee485d-d36a-459c-aa60-015a44c15099)

2. Then I generated an exploitation HTML form to see if the cookies would be sent to the back-end to be destroyed from the HTML form or not. After generating the HTML form, I submitted the Malformed POST request using the form and the cookies were sent through the request even if it was from outside the application.
3. As shown below, I generated a form that simulates the typical request for the **"Misc. Settings Configuration"** to use it in our proof of concept.

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/71189d62-6af2-422f-a636-3fb581ac5592)

4. I discovered that the application accepts the request and the cookies have been sent through the request as seen below in the referer header as soon as we accessed the malicious link to simulate a real victim.

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/0efcdc29-0f02-448d-a650-1d760ba13294)

5. As you can see, the JavaScript code was successfully performed at MiscSettings after being triggered by the payload from the back-end, as seen below:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/cb5d8dbc-e538-47e2-a71c-20f062089bfa)

Because we are able to inject Javascript code, we can hijack the user's session with this attack, which allows an attacker to take over a user's account and get full control of that user in some cases.

At the end of this exploit, you will notice that we went through the following:
- Bypass front-end restriction
- bypass CSRF integration
- Fire up the cross-site scripting to hijack a user's session, which may allow us to take the user's account over.


