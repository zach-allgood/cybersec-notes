
```
Pictures.               5       IN      NS      v0n0.nic.Pictures.
Pictures.               5       IN      NS      v0n1.nic.Pictures.
Pictures.               5       IN      NS      v0n2.nic.Pictures.
Pictures.               5       IN      NS      v0n3.nic.Pictures.
Pictures.               5       IN      NS      v2n0.nic.Pictures.
Pictures.               5       IN      NS      v2n1.nic.Pictures.

Music.                  5       IN      NS      a.nic.Music.
Music.                  5       IN      NS      b.nic.Music.
Music.                  5       IN      NS      c.nic.Music.
Music.                  5       IN      NS      d.nic.Music.

app.inlanefreight.htb.  604800  IN      A       10.129.18.15
internal.inlanefreight.htb. 604800 IN   A       10.129.1.6
mail1.inlanefreight.htb. 604800 IN      A       10.129.18.201
ns.inlanefreight.htb.   604800  IN      A       10.129.34.136

```


```
nmap -sV -T4 10.129.51.92               
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-03-27 14:42 MST
Stats: 0:00:07 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 25.00% done; ETC: 14:43 (0:00:18 remaining)
Stats: 0:01:47 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 75.00% done; ETC: 14:45 (0:00:36 remaining)
Stats: 0:02:33 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 75.00% done; ETC: 14:46 (0:00:51 remaining)
Nmap scan report for 10.129.51.92
Host is up (0.071s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT     STATE SERVICE VERSION
21/tcp   open  ftp?
22/tcp   open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)
53/tcp   open  domain  ISC BIND 9.16.1 (Ubuntu Linux)
2121/tcp open  ftp     ProFTPD
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port21-TCP:V=7.94SVN%I=7%D=3/27%Time=660492EA%P=aarch64-unknown-linux-g
SF:nu%r(GenericLines,9B,"220\x20ProFTPD\x20Server\x20\(ftp\.int\.inlanefre
SF:ight\.htb\)\x20\[10\.129\.51\.92\]\r\n500\x20Invalid\x20command:\x20try
SF:\x20being\x20more\x20creative\r\n500\x20Invalid\x20command:\x20try\x20b
SF:eing\x20more\x20creative\r\n");
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 170.05 seconds
```

