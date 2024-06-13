# Index
[Classification of IP Addresses](#Classification-of-IP-Addresses)

[Cybersecurity Frameworks](#Cybersecurity-Frameworks)

[Common Cyber Attacks)](#Common-Cyber-Attacks)

[OWASP](#owasp)

[OSI Model Layers](#osi-model-layers)

[Cyber Kill Chain](#cyber-kill-chain)

---
## Security Operations Center (SOC)
---
## Classification of IP Addresses

### IPv4 Address Classes

1. **Class A**
   - Range: 0.0.0.0 to 127.255.255.255
   - Subnet Mask: 255.0.0.0
   - Default Subnet Mask: 255.0.0.0

2. **Class B**
   - Range: 128.0.0.0 to 191.255.255.255
   - Subnet Mask: 255.255.0.0
   - Default Subnet Mask: 255.255.0.0

3. **Class C**
   - Range: 192.0.0.0 to 223.255.255.255
   - Subnet Mask: 255.255.255.0
   - Default Subnet Mask: 255.255.255.0

4. **Class D**
   - Range: 224.0.0.0 to 239.255.255.255
   - Used for multicast groups

5. **Class E**
   - Range: 240.0.0.0 to 255.255.255.255
   - Reserved for experimental use

### Private IP Addresses

- **Class A**: 10.0.0.0 to 10.255.255.255
- **Class B**: 172.16.0.0 to 172.31.255.255
- **Class C**: 192.168.0.0 to 192.168.255.255

### Public IP Addresses

- Assigned by the Internet Assigned Numbers Authority (IANA) and used for devices that are accessible over the Internet.

### Static IP Addresses

- Manually assigned to a device and do not change over time.

### Dynamic IP Addresses

- Assigned by a DHCP server and can change over time.

### IPv6 Addresses

- **Structure**: 128-bit address written in hexadecimal and separated by colons.
- **Example**: 2001:0db8:85a3:0000:0000:8a2e:0370:7334
- **Types**: Unicast, Anycast, Multicast
- **Global Unicast Address**: Globally unique and routable on the IPv6 Internet.
- **Link-Local Address**: Used for communication within a single network segment.
- **Unique Local Address**: Used for local communication within a site or between a limited number of sites.

### Cybersecurity Frameworks

1. **NIST Cybersecurity Framework**: Guidelines for identifying, protecting, detecting, responding to, and recovering from cyberattacks.

2. **ISO 27001/27002**: International standards for information security management systems (ISMS).

3. **SOC 2**: Criteria for assessing security, availability, processing integrity, confidentiality, and privacy for cloud service providers.

4. **HIPAA**: Standards for protecting health information.

5. **GDPR**: European Union's regulation focusing on data privacy and protection.

6. **FISMA**: Security requirements for federal agencies.

7. **NERC-CIP**: Cybersecurity standards for electric reliability and critical infrastructure.

8. **CIS Controls**: Actionable best practices to enhance security posture.

9. **COBIT**: Framework for business-IT alignment and governance.

10. **HITRUST CSF**: Tailored cybersecurity framework for the healthcare industry.

11. **NY DFS**: New York's financial security regulation.
---

### Common Cyber Attacks

1. **DDoS Attacks**: Overwhelm a system with traffic to disrupt service.

2. **Malware Attacks**: Includes ransomware, trojans, and spyware that damage or steal data.

3. **Phishing Attacks**: Deceptive emails or messages tricking users into revealing sensitive information.

4. **Man-in-the-Middle Attacks**: Intercepts communication between two parties to eavesdrop or alter the data.

5. **SQL Injection Attacks**:Exploits database vulnerabilities to execute malicious SQL commands.

6. **Zero-Day Exploits**:Exploits unknown software vulnerabilities before they are patched.

7. **Password Attacks**: Attempts to guess or crack passwords to gain unauthorized access, often using brute force methods.

8. **Drive-by Download Attacks**: Installs malware on a user's device through compromised websites without their knowledge.

9. **Cross-Site Scripting (XSS) Attacks**: Injects malicious scripts into web pages viewed by other users.

10. **Rootkits**: Stealthy software that hides its presence and other malware on a system.

11. **DNS Tunneling and Spoofing**: Manipulates DNS queries to bypass security measures or exfiltrate data.

12. **Internet of Things (IoT) Attacks**: Targets vulnerabilities in connected devices to gain access or cause disruption.

13. **Session Hijacking**:Takes over a user's session to impersonate them and gain unauthorized access.

14. **URL Manipulation**: Alters URLs to redirect users to malicious sites or steal information.
---

### OWASP

- **OWASP ASVS**: 
  - A set of security requirements for designing, developing, and testing modern web applications and services.

### OSI Model Layers

1. **Physical Layer (Layer 1)**: 
   - Physical connection and transmission of raw bit streams (e.g., hubs, repeaters, modems, cables).

2. **Data Link Layer (Layer 2)**: 
   - Node-to-node data transfer and error correction (e.g., switches, bridges).

3. **Network Layer (Layer 3)**: 
   - Device addressing and packet forwarding (e.g., IP, routers).

4. **Transport Layer (Layer 4)**: 
   - End-to-end data transfer and error recovery (e.g., TCP, UDP).

5. **Session Layer (Layer 5)**: 
   - Connection management between applications.

6. **Presentation Layer (Layer 6)**: 
   - Data translation and encryption.

7. **Application Layer (Layer 7)**: 
   - Network services for applications (e.g., HTTP, SMTP, FTP).
---

### Cyber Kill Chain

1. **Reconnaissance**: 
   - Gathering information about the target.

2. **Weaponization**: 
   - Creating tailored malware.

3. **Delivery**: 
   - Sending malware to the target.

4. **Exploitation**: 
   - Exploiting vulnerabilities to gain access.

5. **Installation**: 
   - Establishing a foothold on the system.

6. **Command and Control (C2)**: 
   - Remote control of the compromised system.

7. **Actions on Objectives**: 
   - Achieving the attacker's goals (e.g., data theft).
---

8. **Exfiltration**: 
   - Stealing and sending data to the attacker.

9. **Monetization**: 
   - Profiting from stolen data (e.g., selling on the dark web).
