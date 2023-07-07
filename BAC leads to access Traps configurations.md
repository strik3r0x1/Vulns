## Description
Improper access control leads to access and edit Traps configurations affecting Elenos ETG150 FM transmitter running on version 3.12


##### Discoverer: Eslam Kamal (Strik3r) | Cypro AB
##### Vendor of Product: Elenos
##### Affected Product: ETG150 FM transmitter - 3.12


## Introduction
Vertical access controls are mechanisms that restrict access to sensitive functionality that is not available to other types of users. With vertical access controls, different types of users have access to different application functions. For example, an administrator might be able to modify or delete any user's account, while an ordinary user has no access to these actions. Vertical access controls can be more fine-grained implementations of security models designed to enforce business policies such as separation of duties and least privilege.

## POC
In the Senders configuration, the admin user is only permitted to update (SMS, Email). The user can access restricted editable configurations (Traps) that he is not authorized to alter with this vulnerability.

If you used the admin user to access the Senders configuration path, you will see that all of the "Traps" edit buttons are faded and that there is no way to change the values as seen below:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/95f979bf-417b-46ba-b1a2-8982b92f1b8f)

Now try to edit an SMS or Email and see that the URL contains a configuration object id indicator, such as "/event/senders/2/edit."

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/651b812f-4d38-4c59-870d-8909b569f376)

If the user changes this object id to an existing one he will get access to its configuration in our case, this would be "3" which belongs to Traps

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/50a3e4f9-4357-4544-bc17-240fd52013d3)

As you can see this will allow the user to change these values and save them successfully

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/615514b7-449a-446b-8896-6612cc51098f)
