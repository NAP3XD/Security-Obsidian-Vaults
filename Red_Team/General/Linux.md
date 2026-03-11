[Master_Cheatsheet][https://linuxize.com/cheatsheet/]

## Files
### Create Del
```
mkdir	     // Create directory
mkdir -p a/b/c	// Create nested dirs
touch	   // Create empty file
rm	       // Remove file
rm -rf dir	// Remove dir recursively
```
### Info
```
file  // file type
stat  // status
type  // cmd type
whick  // locate cmd
basename  // strip dir path
```
### Viewing
```
cat	   // Display contents
less	// View with pagination
head	// First N lines
tail	// Last N lines
tail -f file	Follow changes
```
### File Search

#### Find
```
find . -name "*.txt"  // file by name
find . -type d    // find dirs
```
#### Locate
```
locate 
```
### Text

#### Grep
```
grep	          // Search in file
grep -r "text" dir	// Search recursively
grep -i "text"	    // Case insensitive
grep -n "text"	   // Show line numbers
grep -v "text"	   // Invert match
```
#### SED
```
sed
sed -i '$d' <file/path.f>      // delete last line of a file

sed 's/old/new/g'	     // Find & replace
sed -i 's/old/new/g'	// In-place replace

```
#### AWK
```
awk

awk '{print $1}'	// Print 1st field
awk -F: '{print $1}'	// Custom delimiter
```
### Text
#### Processing
```
sort file	Sort lines
uniq file	Remove duplicates
wc	Count lines/words
cut	Cut columns
tr	Translate chars
paste	Merge lines
```
#### NL
```
nl <file>   // show number lines
nl -ba /etc/nginx/sites-enabled/default | sed -n '70,105p'   // show lines from 70-105
```
### Compress
```
zip -r a.zip <dirname>   // create zip
unzip a.zip              // extract zip

tar -czvf a.tar.gz dir	// Create tar.gz
tar -xzvf a.tar.gz	  // Extract tar.gz
```
## Admin
```
export <env>   // set env variable 
```
### UserAdmin
```
useradd
userdel
passwd <user>
usermod
su   // switch user 

groupadd
groupdel
```
#### Info
```
whoami  // userame
id    // ID and groups
who   // logged in users
w    // who and what they do 
last  // login history
```


#### systemctl
```
systemctl start/stop/reload
systemctl status 

systemctl enable/disable    // at start up
systemctl is-enabled <service>   // check if enabled at startup

systemctl reboot	// Reboot the system
systemctl poweroff	// Power off the system
systemctl halt	    // Halt the system
systemctl suspend	// Suspend
systemctl hibernate	// Hibernate
```

#### Perms
[cheatsheet][https://linuxize.com/post/chmod-command-in-linux/]

```
chgrp  // change group
chown  // change owner 
```
#### Chmod
```
chmod [OPTIONS] [ugoa…][-+=]perms…[,…] FILE

chmod u+x <file>    // add execute for user 
chmod -x <file>    // remove execute fo all

chmod u=rwx,g=r,o= filename  // stack options 

chmoe o+t <dirname>   // add sticky bit to dir
chmod 1777 dirname    // set sticky bit in num

chmod -R o-w <dirname>  // recursively remove write for others
chmod og= <filename>    // remove all perms for other,group
chmod --reference=f1 f2	// Copy permissions from f1 to f2

chmod u+s <filename>   # or 4755, runs as file owner
chmod g+s /shared/dir   # or 2755, runs as files group
chmod +t /tmp   # or 1777, only owner(f or d) can delete/rename files

 

// common 
chmod 644 file	// Owner read/write; group and others read only
chmod 755 file	// Owner full; group and others read and execute

Chattr -i <file/dir>      // make file immutable 
Lsattr  <file/dir>        // unlock immutable file 

```
r=4
w=2
x=1
noperms=0
stat -c "%a" filename    // check numeric notation





### sysAdmin

#### sysInfo
```
uname -a	// System info
hostname	// Show hostname
uptime	// System uptime
date	// Current date/time
dmesg	// Kernel messages
history	// Command history
```

#### Proc Control
```
kill	   // Terminate process
kill -9 PID	// Force kill
pkill	   // Kill by name
killall name	// Kill all by name
timeout	       // Run with time limit
```
#### Process
```
cmd &   // run in background
bg  // bg current
fg   // bring back process
jobs  // lisst jobs
at   // schedule cmd

ps aux // list all process
htop  // interactive viewer
pstree  // process tree
pgrep   // process by name
pidof   // by PID name
```
#### Disk

```
df     // disk space
du     // dir size
fdisk   // partition table
fsck    // check filesystem 
```
#### Archives
```
tar	                 // Archive files
tar -czvf a.tar.gz dir	// Create tar.gz
tar -xzvf a.tar.gz	   // Extract tar.gz
gzip	              // Compress file
gunzip	              // Decompress file
zip -r a.zip dir	// Create zip
unzip a.zip	       // Extract zip
```
#### SystemUpdate
```
sudo apt update
apt list --upgradable
sudo apt upgrade
sudo apt dist-upgrade
sudo apt autoremove 
```

#### Installs
```
apt install build-essential -y
apt install make -y

// Networking
iproute2 // ip, ipconfig
net-tools  // ifconfig,netstat,route
iputils-ping   // ping
dnsutils  //dns,nslookup,host
traceroute
tcpdump
ethtool
uml-utilities   // set up tun0: tunctl -t tun0

wget // download files
curl  // test HTTP endpoints

apt install -y iputils-ping iproute2 net-tools curl wget whois // starter tools 

```

## Networking
### ifconfig
```
ifconfig <int> <ip/CIDR>   // assign IP to int
ifconfig tun0 192.168.53.1/24    // set up tun0

// add to route table
route add -net <ip/24> <interface>


```
### IP
```
ip -br -c link  // show network ints 
ip -br -c a   // colorized
ip -br -c -6 a  // show ipv6 

ip link show  // show network ints
ip addr show  // who all IP

ip addr add <ip/24> dev <int>  // assign ip to interfae
ip addr del <ip/16> dev <int>  // delete 

ip link set dev <int> up/down // bring int up/down
ip link set dev 

// routing table
ip -c route list // display routing table 
ip route add <ip/25> dev <int>  // add route <ip/24> out <int>
ip route add <int/24> via 192.168.1.1  // send route to gateway
ip route del default  // delete default route

```
### route
```
route       // show routes 
route -6   // show ipv6 routes 
```
### Ping
```
ping -6 -D -w 10 <ip>  // send ipv6 packets for 10 sec w/ timestamps
ping -I eth0 -s 1500 <ip>  // sent 1500 byte packets out of etho0
```
### iptables
```
iptables -F   // clear
iptables -t nat -F   // clear nat

iptables -L   // list filter table
iptables -t nat -L -n -v  // list nat table


// NAT
iptables -t nat -A POSTROUTING -j MASQUERADE -o <interface>

// forwards packets 
sysctl net.ipv4.ip_forward=1
```

### TCPDump
```
sudo tcpdump -ni wlx00c0caad9331 'host 1.1.1.1 and (icmp or tcp port 443)'

// capture traffic to file 
tcpdump -i <interface> -w capture.pcap

// analyze file
tcpdump -r traffic.pcap
tcpdump -r partBclientCapture.pcap -nn -X  // heades/payload/asciII/hex
```
### UFW
[cheatsheet][https://linuxize.com/cheatsheet/ufw/]
```
ufw enable 
ufw status numbered
ufw delete #

ufw deny out on <int> to <ip>     // 152.15.38.65

```
### SS
```
sudo ss -tulpn    // tcp,udp,listening,process/PID/numeric address/port

ss -tulpn | grep :80
ss -tnp 'sport = :443'  // source port expression 
```
## Tools
### RDP
```shell-session
xfreerdp /u:Administrator /p:'[password]' /v:[Target IP] /dynamic-resolution
```
#RDP 
### SMB
[CheatSheet][https://github.com/noobosaurus-r3x/Cheat-sheets/blob/main/SMBClient%20Cheat%20Sheet.md] 
```
smbclient -L //SERVER_NAME -U username

smbclient //SERVER_NAME/SHARE -U username

sudo apt install -y cifs-utils

// must be in /etc/fstab
sudo mount -t cifs //SERVER_NAME/SHARE /mount/here \
  -o username=USERNAME,soft,vers=3.0,noauto,x-systemd.automount

// basic mount cmd (pain if not perment share)
sudo mount -t cifs //SERVER_NAME/SHARE /mount/here -o username=USERNAME

//add to avoid lagging when share not avaliable 
soft,vers=3.0,actimeo=1,echo_interval=10,deadtime=5

 //server/share /mnt/share cifs credentials=/etc/smbcred,vers=3.0,noauto,x-systemd.automount 0 0
 
 sudo umount /mnt/share


```
[[SMB]] #RDP 

### Git

```

Git clone –branch test [http://the](http://the)repo  // clone branch other than main

Git remote -v   // see the origin url 

Git init  // initialize new repo

Git add .
Git add `<file>

Git status // shows current state

Git commit -m “message”

Git push

Git branch -b branch      // to add new branch

Git checkout `<branch>'

Git merge  `<feature_branch`>
git

git config --global user.name "Your New Name"
git config --global user.email "Your New email"

```

### Venv

#### linux
```
Python3 -m venv [name of env “python_env, venv]

Source ./python_env/bin/activate
Deactivate
```


#### Win
```
win_venv/Scripts/activate.bat
```

## SSH
~/.ssh/config
Host, HostName, User, Port, IdentityFile
### ssh
```
ssh user@host
ss host  // use current username

ssh user@host -p 222 -i /dir/file   // custom port and key
ssh -v user#host cmd // run cmd on remote host 
 

```


### SSh-Keys
#key
```
ssh-add    // add default key to agent
ssh-add -l  // list keys in agent
ssh-add ~/.ssh/<keyfile>   // add specific key
ssh-add -d ~/.ssh/<keyfile>   // remove key
ssh-add -D  // remove all keys

ssh-keygen -y -f ~/.ssh/   // show public key
ssh-keygen -R host   // remove host from known_hosts

ssh-keygen -o -t rsa -b 4096 -C “email or comment”  // 4096 bit, w/ comment
ssh-keygen -t ed25519 -C "your_email@example.com"

```
### SCP
```
scp file user@host:/path/   // copy file to remote host at path
scp -r dir user@host:/path/   // copy dir recursively
```
### Tunneling 
```
ssh -L 8080:localhost:80 user@host	// Local port forwarding
ssh -R 8080:localhost:80 user@host	// Remote port forwarding
ssh -D 1080 user@host	// SOCKS proxy (dynamic)
ssh -N -L 8080:localhost:80 user@host	// Tunnel only (no shell)
ssh -f -N -L 8080:localhost:80 user@host	// Background tunnel
```


## Debug

### Port testing
#ss
```

sudo ss -tnlp | grep postgres       // find port service running on

```

### Files
```
// delete last line of a file
sed -i '$d' /etc/resolv.conf      

// open line number #
Vim +# /dadir/dafile.txt    

nl  // number lines of files  
// showlines from 70-105
nl -ba /etc/nginx/sites-enabled/default | sed -n '70,105p'   
```
  

## Web server Hosting
#php 
```
// can accept POST request 
php -S localhost:8000

Python3 -m http.server <port>

```
