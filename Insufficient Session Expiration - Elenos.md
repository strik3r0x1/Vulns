## Description

insufficient session expiration allowing users to change transmitter configuration and data even after logging out from their account affecting Elenos ETG150 FM transmitter running on version 3.12

##### Discoverer: Eslam Kamal (Strik3r) | Cypro AB
##### Vendor of Product: Elenos
##### Affected Product: ETG150 FM transmitter - 3.12


## Introduction
Through this vulnerability, if the attacker was able to obtain the user's session in some way, he could access the user's account and data even if the user logged out of the application, which would make the attacker persist in the user's account.

## POC

login with Admin account, navigate to the "Preference" endpoint, and intercept the save request with any proxy tool.
![image](https://github.com/strik3r0x1/Vulns/assets/94288990/46a94933-dc79-493f-bd6a-e00b5ba6206b)

in the previous image, we noticed that the Temperature Unit is set to "C" and the Format Number is set to "Extended"

Notice that the options for Temperature Unit config are:

* C
* F

And options for Format Number are:

* Extended
* K
After intercepting the request, logout from the account:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/909016ad-3949-4b96-8398-0b69fe2651e4)


Try changing the Temperature Unit to "F" and Number Format to "K" as seen below and running the request. If there is any protection for session expiration we shouldn't be able to update any configuration after logging out.

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/c2004432-2190-4fc5-9a3d-0ce2ef10a2cd)

Re-login to the same account and you'll see that the Format Number and Temperature Unit parameters have been modified.

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/70c90a6f-85e4-438b-bb40-52c49ff53220)
