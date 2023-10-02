## Description
Insecure Direct Object Reference (IDOR) leads to events profiles access affecting Elenos ETG150 FM transmitter running on version 3.12

##### Discoverer: Eslam Kamal (Strik3r)
##### Vendor of Product: Elenos
##### Affected Product: ETG150 FM transmitter - 3.12


## Introduction
Insecure Direct Object References (IDOR) occur when an application provides direct access to objects based on user-supplied input. As a result of this vulnerability attackers can bypass authorization and access resources in the system directly. Such resources can be database entries belonging to other users, files in the system, and more. This is caused by the fact that the application takes user supplied input and uses it to retrieve an object without performing sufficient authorization checks.


## POC

we noticed that an endpoint shows the event alarm profiles as shown below:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/1bfc2d24-7a52-49b4-9644-bb32d3866792)


But when hitting the search button to seek for profiles or alarms, it gives the low-privilege user nothing as an indicator that there are no alarms set for this profile, "Default Profile," as you can see:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/d3cef324-a01e-4aaf-9e89-5bd558786f76)

We noticed that there is a profile id being sent in a REST URL, so we manipulated the profile id to set the id as "1" instead of "2" to test if the access controls for event profiles are well and securely set, but we found that the low-privilege user can access them as shown below:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/e96e139d-388b-40ec-89f8-55cbc7db6e30)
