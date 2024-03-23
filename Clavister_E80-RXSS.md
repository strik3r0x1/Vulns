# ===== Reflected-XSS chained with CSRF at Clavister E80 Firewall =====
##### Discoverer: [Eslam Kamal (Strik3r)](https://www.linkedin.com/in/eslam-kamal/)
##### Vendor of Product: Clavister
##### Affected Product: Clavister E80 - EagleSeries
-----------------------------------
![image](https://github.com/strik3r0x1/Vulns/assets/94288990/338e9f93-aff1-426f-818e-f9c7bd32e394)

## Description
Reflected XSS chained with CSRF poses a threat to Clavister E80 Firewall-protected web applications. In this scenario, attackers inject malicious scripts into the application, which execute in users' browsers, potentially leading to unauthorized actions like data theft or manipulation. While the firewall provides network security, it may not safeguard against these specific web application vulnerabilities. Mitigation strategies include secure coding practices, such as input validation and output encoding, as well as implementing anti-CSRF tokens and conducting regular security assessments.


## POC
Steps To Reproduce:
