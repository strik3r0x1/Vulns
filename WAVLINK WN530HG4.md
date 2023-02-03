# Summary:
WAVLINK WN530HG4 AC1200 High Power Dual Band Gigabit Router (WL-WN530HG4) devices running firmware version (M30HG4.V5030.201217) have an access control issue, allowing unauthenticated attackers to download configuration data and log files and obtain admin credentials.

## Vendor:
* Wavlink

## Affected Product:
* WL-WN530HG4

## Version:
* M30HG4.V5030.201217


# Details:
When an unauthenticated attacker requests /cgi-bin/ExportLogs.sh this will lead to downloading all configurations and Admin Credentials and accessing the Device Dashboard

![image](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FNXCJWNoU0PexwJ6yBpmG%2Fuploads%2FWBbBRpghb8E5OUvJAZsU%2Fcve1.png?alt=media&token=8d1d548c-465d-43a7-a10a-d00af0c2d6b9)

![image](https://user-images.githubusercontent.com/94288990/216494855-abdea904-a895-4533-8ca6-5c7b2b2a0959.png)
