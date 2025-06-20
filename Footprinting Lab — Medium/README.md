# Footprint Lab — Medium

IP - 10.129.38.229


## Scanning & Enumeration


nmap - 
```
Discovered open port 135/tcp on 10.129.38.229
Discovered open port 139/tcp on 10.129.38.229
Discovered open port 111/tcp on 10.129.38.229
Discovered open port 3389/tcp on 10.129.38.229
Discovered open port 445/tcp on 10.129.38.229
Discovered open port 49667/tcp on 10.129.38.229
Discovered open port 49678/tcp on 10.129.38.229
Discovered open port 2049/tcp on 10.129.38.229
Discovered open port 49666/tcp on 10.129.38.229
Discovered open port 49681/tcp on 10.129.38.229
Discovered open port 47001/tcp on 10.129.38.229
```

* Ports that caught my attention are 445 (SMB), 2048 (NFS), and 3389 (RDP).

```
445/tcp  open  microsoft-ds?
2049/tcp open  mountd        1-3 (RPC #100005)
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: WINMEDIUM
|   NetBIOS_Domain_Name: WINMEDIUM
|   NetBIOS_Computer_Name: WINMEDIUM
|   DNS_Domain_Name: WINMEDIUM
|   DNS_Computer_Name: WINMEDIUM
|   Product_Version: 10.0.17763
|_  System_Time: 2025-06-19T23:49:51+00:00
|_ssl-date: 2025-06-19T23:50:00+00:00; 0s from scanner time.
| ssl-cert: Subject: commonName=WINMEDIUM
| Issuer: commonName=WINMEDIUM
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2025-06-18T21:35:20
| Not valid after:  2025-12-18T21:35:20
| MD5:   c5a6:261e:9604:1a76:5a3c:2afd:d458:a32c
|_SHA-1: bb11:731a:a500:4c76:5211:aef0:7696:c5f5:dc1b:89a3
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: Microsoft Windows 10 1709 - 21H2 (97%), Microsoft Windows Server 2019 (96%), Microsoft Windows Server 2016 (95%), Microsoft Windows 10 1903 (93%), Microsoft Windows Server 2012 (93%), Windows Server 2019 (93%), Microsoft Windows Server 2022 (93%), Microsoft Windows Vista SP1 (93%), Microsoft Windows 10 (93%), Microsoft Windows 10 21H1 (92%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=263 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2025-06-19T23:49:52
|_  start_date: N/A
```


## Port 2049 (NFS) Enumeration


![image](https://github.com/user-attachments/assets/39ab7025-0c2e-469b-a65d-5fbf6b939f45)


* Found directory ```/TechSupport```
* I created a directory in my machine called "NFS" and ran this command to move /TechSupport to my machine - ```sudo mount -t nfs 10.129.38.229:/TechSupport ./NFS/ -o nolock```
* I received "cd: permission denied: NFS" so I switched to root user by running ```sudo su```
* Now I was able to review the files inside the /TechSupport but there were to many of them and going through each one would take forever so I ran ```ls -la``` to view which one has information inside

![image](https://github.com/user-attachments/assets/200f568b-b272-4341-868b-ba727ec43339)


* Inside ```ticket4238791283782.txt``` I found username and password:


![image](https://github.com/user-attachments/assets/3626fef0-a370-4925-83e4-5f12c51417e2)



## Port 3389 (RDP) Enumeration

* I used the username and password to remote in using RDP and found ```important.txt``` file.


![image](https://github.com/user-attachments/assets/b3020bf5-b192-4ef8-8ba7-400e55fcd308)


* Tried to RDP again but this time I used Administrator login credentials and added the new password that I found - ```xfreerdp3 /v:10.129.38.229 /u:Administrator /p:’87N1ns@slls83'```
* After successfully remoting in, I was able to easily access the SQL Server and found username "HTB" with the password inside table ```dbo.devsacc```.


![image](https://github.com/user-attachments/assets/bd9b9cc8-157a-4ddc-b4ba-5e9fb214efd8)



![image](https://github.com/user-attachments/assets/dd6b2459-63a1-4cf9-958f-05de416a9dca)
