# About

# Cmds

```
Nmap --help  

```

## Host Discovery 
```
sudo nmap 10.129.2.0/24 -sn -oA tnet | grep for | cut -d" " -f5
```
Give network in CIDR
-sn        Disable port scanning
-oA    stores results in all formats

-iL <hosts.lst>     // scan predfined list

Can provide multiple Ips 

-PE        // ping scan
--packet-trace       // shows all packets sent and received

## Discovering Open ports
-A Agressive, service, OS, traceroute, default scripts 
-sT   is default, uses three-way handshake TCP
-sU   UDP scan only get a response if app configured to do so
-p-   scans all ports
-p 22,25,26 
-p 25-30
-F   fast port scan top 100
-n disable DNS resolution
--disable-arp-ping  disables ARP ping
-Pn   Disables ICMP Echo request 

--top-ports=`[number]`

scans top 1000 TCP ports with -sS (Syn scan)

## Service Enumeration
-sV scan port for services and versions 
-O  operating sys
script banner.nse   
-sC   enumerate databases services on a target 

## Scripts
```shell-session
sudo nmap <target> -sC
sudo nmap <target> --script <category> 
sudo nmap <target> --script <script-name>,<script-name>,<...>
```

|**Category**|**Description**|
|---|---|
|`auth`|Determination of authentication credentials.|
|`broadcast`|Scripts, which are used for host discovery by broadcasting and the discovered hosts, can be automatically added to the remaining scans.|
|`brute`|Executes scripts that try to log in to the respective service by brute-forcing with credentials.|
|`default`|Default scripts executed by using the `-sC` option.|
|`discovery`|Evaluation of accessible services.|
|`dos`|These scripts are used to check services for denial of service vulnerabilities and are used less as it harms the services.|
|`exploit`|This category of scripts tries to exploit known vulnerabilities for the scanned port.|
|`external`|Scripts that use external services for further processing.|
|`fuzzer`|This uses scripts to identify vulnerabilities and unexpected packet handling by sending different fields, which can take much time.|
|`intrusive`|Intrusive scripts that could negatively affect the target system.|
|`malware`|Checks if some malware infects the target system.|
|`safe`|Defensive scripts that do not perform intrusive and destructive access.|
|`version`|Extension for service detection.|
|`vuln`|Identification of specific vulnerabilities.|
## Saving Results
-oN    Normal .nmap
-oG     Grepable .gnmap
-oX     XML .xm.
## Time-To-Live TTL
128 Windows
64 Linux
256 Cisco

#ttl

## Misc
--max-retries   default is 10
--min-rate 300     sets min number of packets to send per second 
--stats-every=`[number]`s   (7s)
-v     verbosity level 
-vv    
--reason    display reason a port in a particular state

Decoys
-D generate random IP address in IP headers 

|`-D RND:5`|Generates five random IP addresses that indicates the source IP the connection comes from.|

-S manually specify source IP address 
-e `<interface>` sends all requests though spec interface 
**Timing**
- `-T 0` / `-T paranoid`
- `-T 1` / `-T sneaky`
- `-T 2` / `-T polite`
- `-T 3` / `-T normal`
- `-T 4` / `-T aggressive`
- `-T 5` / `-T insane`

Timeouts

|`--initial-rtt-timeout 50ms`|Sets the specified time value as initial RTT timeout.|
|`--max-rtt-timeout 100ms`|Sets the specified time value as maximum RTT timeout.|
## Port States
| **State**          | **Description**                                                                                                                                                                                         |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `open`             | This indicates that the connection to the scanned port has been established. These connections can be **TCP connections**, **UDP datagrams** as well as **SCTP associations**.                          |
| `closed`           | When the port is shown as closed, the TCP protocol indicates that the packet we received back contains an `RST` flag. This scanning method can also be used to determine if our target is alive or not. |
| `filtered`         | Nmap cannot correctly identify whether the scanned port is open or closed because either no response is returned from the target for the port or we get an error code from the target.                  |
| `unfiltered`       | This state of a port only occurs during the **TCP-ACK** scan and means that the port is accessible, but it cannot be determined whether it is open or closed.                                           |
| `open\|filtered`   | If we do not get a response for a specific port, `Nmap` will set it to that state. This indicates that a firewall or packet filter may protect the port.                                                |
| `closed\|filtered` | This state only occurs in the **IP ID idle** scans and indicates that it was impossible to determine if the scanned port is closed or filtered by a firewall.                                           |
## Output Understanding
```shell-session
cat tnet.minrate300 | grep "/tcp" | wc -l
```
will count open ports 

## Firewalls, IDS/IPS
#firewall
-sA  TCP ACK scan is harder to filter for firwalls than -Ss Syn scan
--source-port 53  trick firewall by using DNS port 
|`-D RND:5`|Generates five random IP addresses that indicates the source IP the connection comes from.|
Errors to look for:
- Net Unreachable
- Net Prohibited
- Host Unreachable
- Host Prohibited
- Port Unreachable
- Proto Unreachable

## DNS Proxy
#dns
Nmap performs a revese DNS resolution 

specify DNS servers 
--dns-server `<ns>`,`<ns1>`
--source-port 53  trick firewall by 