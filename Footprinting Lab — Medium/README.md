# Footprinting Lab — Medium

IP - 10.129.38.229


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









![image](https://github.com/user-attachments/assets/bd9b9cc8-157a-4ddc-b4ba-5e9fb214efd8)



![image](https://github.com/user-attachments/assets/dd6b2459-63a1-4cf9-958f-05de416a9dca)
