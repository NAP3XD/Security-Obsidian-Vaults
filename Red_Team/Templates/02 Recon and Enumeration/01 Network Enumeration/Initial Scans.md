## Initial Scans

#### TCP
**IP**
```bash
mkdir nmap && sudo nmap -Pn -p- -vv <% tp.frontmatter["RHOSTS"] %> -oN nmap/<% tp.frontmatter["RHOSTS"] %>-tcp-ports && ports=$(grep '^[0-9]' nmap/<% tp.frontmatter["RHOSTS"] %>-tcp-ports  | cut -d '/' -f 1 | tr '\n' ',' | sed s/,$//) && sudo nmap -sCV -Pn -p $ports -vv <% tp.frontmatter["RHOSTS"] %> -oA nmap/<% tp.frontmatter["RHOSTS"] %>-tcp-scripts-versions 
```

**Domain**
```bash
mkdir nmap && sudo nmap -Pn -p- -vv <% tp.frontmatter["VHOST"] %> -oN nmap/<% tp.frontmatter["VHOST"] %>-tcp-ports && ports=$(grep '^[0-9]' nmap/<% tp.frontmatter["VHOST"] %>-tcp-ports | cut -d '/' -f 1 | tr '\n' ',' | sed s/,$//) && sudo nmap -sCV -Pn -p $ports -vv <% tp.frontmatter["VHOST"] %> -oA nmap/<% tp.frontmatter["VHOST"] %>-tcp-scripts-versions
```

#### UDP

**IP**
```shell
sudo nmap -sU -Pn -p- -vv <% tp.frontmatter["RHOSTS"] %> -oA nmap/<% tp.frontmatter["RHOSTS"] %>-udp-ports && ports=$(grep '^[0-9]' nmap/<% tp.frontmatter["RHOSTS"] %>-udp-ports | cut -d '/' -f 1 | tr '\n' ',' | sed s/,$//) && nmap -sCV -sU -p $ports -vv <% tp.frontmatter["RHOSTS"] %> -oA nmap/<% tp.frontmatter["RHOSTS"] %>-udp-scripts-versions
```

**Domain**
```shell
sudo nmap -sU -p- -Pn -vv <% tp.frontmatter["VHOST"] %> -oA nmap/<% tp.frontmatter["VHOST"] %>-udp-ports && ports=$(grep '^[0-9]' nmap/<% tp.frontmatter["VHOST"] %>-udp-ports | cut -d '/' -f 1 | tr '\n' ',' | sed s/,$//) && nmap -sCV -sU -p $ports -vv <% tp.frontmatter["VHOST"] %> -oA nmap/<% tp.frontmatter["VHOST"] %>-udp-scripts-versions 
```

---
### Hosts

#### Active Checks

##### Nmap
```shell
sudo nmap -sn <% tp.frontmatter["RHOSTS"] %> | grep "Nmap scan report for" | awk '{print $5}' | tee -a hosts.txt
```
##### FPing
```shell
fping -asgq <% tp.frontmatter["RHOSTS"] %>
```


#### Nmap Scanning
##### TCP

```shell
mkdir nmap && sudo nmap -Pn -p- -vv -iL hosts.txt -oN nmap/tcp-hosts-ports && ports=$(grep '^[0-9]' nmap/tcp-hosts-ports | cut -d '/' -f 1 | tr '\n' ',' | sed s/,$//) && nmap -sCV -Pn -p $ports -vv -iL hosts.txt -oA nmap/tcp-hosts-scripts-versions 
```

##### UDP

```shell
sudo nmap -sU -Pn -p- -vv -iL hosts.txt -oN nmap/udp-hosts-ports && ports=$(grep '^[0-9]' nmap/udp-hosts-ports | cut -d '/' -f 1 | tr '\n' ',' | sed s/,$//) && nmap -sU -sCV  -Pn -p $ports -vv -iL hosts.txt -oA nmap/udp-hosts-scripts-versions 
```
