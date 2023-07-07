## Description 

User enumeration via profile page edit affecting Elenos ETG150 FM transmitter running on version 3.12

##### Discoverer: Eslam Kamal (Strik3r) | Cypro AB
##### Vendor of Product: Elenos
##### Affected Product: ETG150 FM transmitter - 3.12

## Introduction
The malicious actor is looking for differences in the server's response based on the validity of submitted credentials. The login form is a common location for this type of behavior. When the user enters an invalid username and password, the server returns a response saying that user "Cypro" does not exist. A malicious actor would know that the problem is not with the password but that this username does not exist in the system. On the other hand, if the user enters a valid username with an invalid password and the server returns a different response that indicates that the password is incorrect, the malicious actor can then infer that the username is valid. Ways that attackers can use the enumeration to their advantage are uncountable, and the method in this report is one of the ways that attackers can use this functionality to attack the application or the system to get information from inside.


## POC

the application has three ways to respond to a user state, whether it exists or not:

* 200 => requested user exists and the user has access to it.
* 302 => requested user exists but the user has no access to it.
* 404 => the user is not exists in the application's database.

With this information, a low-privilege user can enumerate user identifiers to check:

* how many users are exists
* what are the identifiers for each user
* the logic of counting the user identifiers

In the image below, you can see the low-privilege user trying to access his profile to edit it, and the user identifier here is "1" as highlighted in the REST URL:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/a3a950af-ad22-45db-8b9c-98e6ff32a3f8)

When we tried the requested unexisting user identifier, which is "100,"  we found that the server responded with "404," as you can see below:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/73a77fdb-98c1-4083-8630-dc070c6e04f5)

When trying to access an existing user, the application responds with a "302" status code as an indicator that the user exists but the current user doesn't have access to view its information:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/68a5d5d4-4802-4b9a-8118-5e5dd7a75756)

As a last step, we brute-forced the identifiers and extracted the following user identifiers, as shown below:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/12c82077-fdc8-410c-bb33-89ce56cf8415)

