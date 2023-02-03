# Summary: 

WAVLINK QUANTUM T8 - AC3000 MU-MIMO Tri-band (WL-WN533A8) devices running firmware version (M33A8.V5030.190716) have an access control issue, allowing unauthenticated attackers to download configuration data and log files and obtain admin credentials.

## Vendor:
* Wavlink

## Affected Product:
* WL-WN533A8

## Version:
* M33A8.V5030.190716


# Details:

When an unauthenticated attacker requests /cgi-bin/ExportLogs.sh this will lead to downloading all configurations and Admin Credentials and accessing the Device Dashboard

## POC
![image](https://user-images.githubusercontent.com/94288990/216495493-62bdc084-81a1-4c28-b401-856c869405a6.png)

![image](https://user-images.githubusercontent.com/94288990/216495546-6d34ca59-e42f-466f-b121-bac4a707d0f2.png)
