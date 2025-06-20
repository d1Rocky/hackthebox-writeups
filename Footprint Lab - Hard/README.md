# Footprint Lab - Hard


IP - 10.129.251.220 


## Scanning & Enumeration


nmap - 
```
Discovered open port 143/tcp on 10.129.202.20
Discovered open port 110/tcp on 10.129.202.20
Discovered open port 22/tcp on 10.129.202.20
Discovered open port 995/tcp on 10.129.202.20
Discovered open port 993/tcp on 10.129.202.20
```
* Didn't find anything useful from TCP scan
* Found port SNMP (161) open using UDP scan

```
PORT    STATE SERVICE
161/udp open  snmp
```


* Used tool ```snmpwalk``` to find username and password


![image](https://github.com/user-attachments/assets/bd322157-2a10-4ba0-ada8-d19943fb153d)



## Port 143 (IMAP)

* Successfully found files inside IMAP port using username: tom and password: NMds732Js2761


![image](https://github.com/user-attachments/assets/3c41d11b-ae4c-4fb5-a94e-d3ab75bcb573)


