
- Ran nmap and found port 22 and port 80 open
- Visited port 80 and found the grav-admin directory
- Visited grav-admin directory and found a Readme for Grav
- Googled Grav Exploit and found an unauthenticated YAML write/update
	- https://www.exploit-db.com/exploits/49973
- Updated python script to include target IP/grav-admin as target
- Updated base64 to call my IP on port 4444
- Waited for cron to run and trigger reverse shell
- Once reverse shell is opened, started a web server and downloaded linpeas.sh from my local env to the target machine using wget
- Ran linpeas.sh on target environment
- Found cronjob but eventually decided it could be a rabbit hole and pivoted
- Looked for SUID escalation possibilities
	- `find / -perm -u=s -type f 2>/dev/null`
- Found php7.4 and looked for PHP in GTFObins
- Found privesc for PHP in GTFObins, ran on www-data, got root shell
- Found root flag in /root/flag.txt and that put box to 100%