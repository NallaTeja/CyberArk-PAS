Title: DR replication Steps for syslogs  
Taken example IP address below for better understand.

Primay VIP - 10.10.12.171
- Active Node: 10.10.12.168
- Passive Node: 10.10.12.167

![image](https://github.com/user-attachments/assets/8e0d5e27-5377-4a14-990f-bf79782dc5f1)

Seconday VIP - 192.168.48.202
- Active Node: 192.168.48.200
- Passive Node: 192.168.48.201

![image](https://github.com/user-attachments/assets/954f85c7-f6e3-4145-9350-563f82fb84be)

---

Steps to be followed:- 

1. **Secondary node** Loin into the Passive Node: 192.168.48.201
2. Turn OFF CVM
3. Loin into the Active Node: 192.168.48.200
4. Turn OFF CVM
5. **Primary Node** login into the Passive Node: 10.10.12.167
6. Update the dbparm.ini file path C:\Program Files (x86)\PrivateArk\Server
   Example:- C:\Program Files (x86)\PrivateArk\Server\Syslog. (Sample will be available copy that update accourdindly)
~~~
[SYSLOG]
SyslogTranslatorFile=Syslog\PTA.xsl
SyslogServerPort=<port number>
SyslogServerIP=<server IP>
SyslogServerProtocol=UDP
SyslogMessageCodeFilter=295,308,7,24,31,428,361,372,373,359,436,412,411,300,302,294,427
UseLegacySyslogFormat=No
~~~
7. **Primary Node** login into the Active Node: 10.10.12.168
8. Switch the nodes (Active becomes passive; Passive become active)
9. Update dbparm.ini file for Node: 10.10.12.168
10. Login into the Node: 10.10.12.167 Switch over (Back to normal)
11. **Secondary node** Loin into the Active Node: 192.168.48.200
12. update the dbparm.ini file
13. Open Disk management make storage disk Active
14. Update padr.ini remove last 2 lines; Full replication make sure failover mode is NO
15. Start the CVM for Node: 192.168.48.200
16. Verfiy padr logs to check for full replicaitons
17. **Secondary node** Loin into the Passive Node: 192.168.48.201
18. Update dbparm.ini
19. Start the CVM for Node: 192.168.48.201
20. After 2 hrs verfiy padr logs in *Secondary node* - Active Node: 192.168.48.200
