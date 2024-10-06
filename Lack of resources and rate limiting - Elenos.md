## Description
Lack of resources and rate limiting on Elenos Login leads to Brute-Force login credentials


##### Discoverer: Eslam Kamal (Strik3r)
##### Vendor of Product: Elenos
##### Affected Product: ETG150 FM transmitter - 3.12


## Introduction
Lack of resources and rate limiting is when the application does not restrict the number or frequency of requests from a particular client. So a  client can make thousands or even more requests per second, or request hundreds or thousands of data records at once, and the application will still try to fulfill these requests. In some cases, the lack of resources and rate-limiting are not an issue. But sometimes, they could allow attackers to do something more. For example, in our case, we were able to brute force the admin/user password that is required to access the panel. This means if we were able to guess the right password, we were able to enter the application by brute forcing it.

## POC

if the attackers tries to enter any fake password during login he will get "Invalid username or password" response:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/94513aa1-d648-4fb5-9a12-13a2e45b1f44)

in order to simulate a real attacker brute-forcing the login panel we were able to send approximately 165 requests in which we attempted to brute force the password without getting blocked:

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/c19641da-57a9-45e8-a6c7-57d573c6d328)

By observing the request status, attackers can make hundreds or even thousands of requests without being blocked in order to obtain the valid password. In the worst-case scenario, attackers could use this to cause a denial of service (DoS)

