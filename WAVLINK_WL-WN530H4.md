# Summary: 

WAVLINK Aerial G - AC1200 High Power Dual Band Wireless Router (WL-WN530H4) devices running firmware version (M30H4.V5030.210121) have an access control issue, allowing unauthenticated attackers to download configuration data and log files and obtain admin credentials.

## Vendor:
* Wavlink
## Affected Product:
* WL-WN530H4
## Version:
* M30H4.V5030.210121

# Details:

When an unauthenticated attacker requests /cgi-bin/ExportLogs.sh this will lead to downloading all configurations and Admin Credentials and accessing the Device Dashboard.

1. Check Application Device Version:

![image](https://user-images.githubusercontent.com/94288990/216496206-90767e70-0ed9-4df4-9413-c84e00535d2a.png)

2. request the vulnerable component.

![image](https://user-images.githubusercontent.com/94288990/216496406-f25b1fa7-e78e-4823-afb3-a1765c663f40.png)

3. Accessing Admin Dashboard:

![image](https://user-images.githubusercontent.com/94288990/216496506-4e7bd203-35d3-4072-9d92-389f449001af.png)
