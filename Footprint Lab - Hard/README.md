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

* Found files inside IMAP port using curl command


![image](https://github.com/user-attachments/assets/3c41d11b-ae4c-4fb5-a94e-d3ab75bcb573)


* Logged into IMAP using this command - ``` openssl s_client -connect 10.129.251.220:imaps ```
* Successfully logged into user tom

![image](https://github.com/user-attachments/assets/290810fd-57d9-4c14-9700-c975ab9da25b)


* Found inside "INBOX" rsa key for SSH


## Port 22 (SSH)

* Created a file and pasted the rsa key inside and then I set the permissions of the file to ```chmod 600```
* Successfully logged into user tom using SSH


![image](https://github.com/user-attachments/assets/c9d742f9-c19c-4417-b62a-bff3c565131f)


* User id shows that tom can access mysql. Used this information to access mysql by running ```mysql --user=tom -p```


![image](https://github.com/user-attachments/assets/a18b1227-a5b3-4496-97c9-c01b2885b399)



* Successfully found HTB user and password using those commands inside mysql:


```
SHOW DATABASES;
USE USERS;
SHOW TABLES;
SELECT * FROM users;
```


![image](https://github.com/user-attachments/assets/7c73b6e3-b270-4526-87b2-94f77ea646e6)

 
