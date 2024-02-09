## Description
GARO GLB+ T2EV7,4KW M AR L wallbox is a smart and high-end charging solution for electric vehicles (EVs). It’s equipped with features like dynamic load balancing, DC-fault protection, and RFID functionality was discovered that it vulnerable to Stored . This vulnerability poses a serious risk to the security and integrity of the web portal and its users. 
The stored XSS vulnerability allows attackers to inject malicious JavaScript code into specific fields or content areas of the web portal. This code is then stored on the server and executed whenever a user accesses the affected page, potentially leading to unauthorized access, data theft, or other malicious actions.

##### Discoverer: Eslam Kamal (Strik3r)
##### Vendor of Product: GARO
##### Affected Product: GLBDCMB-T274WO-A


## POC

1.	Navigate to http://<host>/serialweb/index.jsp#settings and you will see the device configuration without any authentication 
2.	Click on “Software Updates / Identification” and select any wallbox and click on “Edit”



