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


* Used tool snmpwalk to find user Tom


![image](https://github.com/user-attachments/assets/3b845965-5747-47c5-b1be-6610fc4dacc9)
