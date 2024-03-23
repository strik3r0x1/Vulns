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

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/7fd67412-fb72-450a-a71f-59dac9e20dd9)

So, to trigger cross-site script code as shown below, we intercepted the Misc Settings Configuration HTTP POST request and changed the values of 8 parameters:
"WatchdogTimerTime","BufFloodRebootTime","MaxPipeUsers","AVCache Lifetime","HTTPipeliningMaxReq","Reassembly MaxConnections","Reassembly MaxProcessingMem" and "ScrSaveTime".

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/6747eec7-7cc1-4610-8fa2-9af5899e9996)

2. Then I generated an exploitation HTML form to see if the cookies would be sent to the back-end to be destroyed from the HTML form or not. After generating the HTML form, I submitted the Malformed POST request using the form and the cookies were sent through the request even if it was from outside the application.
3. As shown below, I generated a form that simulates the typical request for the **"Misc. Settings Configuration"** to use it in our proof of concept.

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/979efbbb-339a-4051-9db5-f0d9ac727b40)

4. I discovered that the application accepts the request and the cookies have been sent through the request as seen below in the referer header as soon as we accessed the malicious link to simulate a real victim.

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/ce23cecc-7d79-4efd-9d09-de019bd6b35e)

5. As you can see, the JavaScript code was successfully performed at MiscSettings after being triggered by the payload from the back-end, as seen below:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/d5c499bc-5d6c-4fcd-b590-c449a49cbd8f)

Because we are able to inject Javascript code, we can hijack the user's session with this attack, which allows an attacker to take over a user's account and get full control of that user in some cases.

At the end of this exploit, you will notice that we went through the following:
- Bypass front-end restriction
- bypass CSRF integration
- Fire up the cross-site scripting to hijack a user's session, which may allow us to take the user's account over.


