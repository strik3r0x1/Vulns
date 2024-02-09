## Description
GARO GLB+ T2EV7,4KW M AR L wallbox is a smart and high-end charging solution for electric vehicles (EVs). It’s equipped with features like dynamic load balancing, DC-fault protection, and RFID functionality was discovered that it vulnerable to Stored . This vulnerability poses a serious risk to the security and integrity of the web portal and its users. 
The stored XSS vulnerability allows attackers to inject malicious JavaScript code into specific fields or content areas of the web portal. This code is then stored on the server and executed whenever a user accesses the affected page, potentially leading to unauthorized access, data theft, or other malicious actions.

##### Discoverer: Eslam Kamal (Strik3r)
##### Vendor of Product: GARO
##### Affected Product: GLBDCMB-T274WO-A

## Poc video
https://drive.google.com/file/d/1spsElvU8rgCs4gUxc662SCBjTI9VAqth/view?usp=sharing

## POC

1.	Navigate to http://<host>/serialweb/index.jsp#settings and you will see the device configuration without any authentication 
2.	Click on “Software Updates / Identification” and select any wallbox and click on “Edit”

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/ffda9142-7e47-46bd-8f64-009acbbeb118)

3.	Now, fill in any data in the “Reference” textbox and click on update. And capture this HTTP request with any proxy such as Burpsuit
4.	Modify the “Reference” json value to any XSS payload and send the request 

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/fcd8e415-b33e-458e-8193-e9d023b221a3)

5.	Now, if you tried to back to device portal you will notice the “XSS” popup appeared

![image](https://github.com/strik3r0x1/Vulns/assets/94288990/e82fe461-9d84-4a6b-b058-629973988776)

