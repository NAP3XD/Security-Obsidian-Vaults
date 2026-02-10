## CMDs

Docker –help
Docker <command> –help


## Docker compose

docker compose up -d      // spin up containers

docker compose -f <yourfile.yml> up -d           // provide file


### Basic containers tools

apt update

apt install -y iputils-ping iproute2 net-tools curl wget   // starter tools 

  

Kali tools

apt update

apt install -y kali-linux-headless

apt update

apt install -y kali-linux-headless net-tools iproute2 iputils-ping curl wget tcpdump nmap gobuster ffuf nikto

  
  
  
  
  

Docker compose start

Docker compose stop        // stop containers 

Docker compose down       // tear down the env

  
  

Docker ps    // running containers

Docker ps -a    // all containers

Docker stop <container>      // stop containers

Docker rm <container>     // delete containers

Docker inspect             // show JSON details 

Docker logs

Docker top               // running processes 

  

Docker cp            // copy files to and from host/container

docker cp myfile.txt <container>:/root/          // 

  
  

Docker port           // port mappings

Docker stats          // show cpu/mem/ etc

Docker system df     // show disk usages

  
  

docker exec -it <container> bash   // enter terminal 

  
  
  
  

Networks

docker network inspect <net-name>

  

docker network create --driver bridge --subnet 192.168.10.0/24 <net-name>

  

Docker images

Docker inspect <img-name>

docker images -f dangling=true        // see unused imgs

docker rmi <image-name-or-id>       // remove imgs

  
  
  

Custom img

Mkdir <custom-img> && cd <custom-img>

Nano Dockerfile                // config file

docker build -t custom-kali .        // build img

  
  
  

Tools:

- iproute2 — provides ip, the modern replacement for ifconfig
    
- net-tools — legacy tools like ifconfig, netstat, route
    
- iputils-ping — gives you ping and ping6
    
- dnsutils — includes dig, nslookup, host
    
- traceroute — trace packet paths
    
- curl — test HTTP endpoints
    
- wget — download files
    
- tcpdump — packet capture inside the container
    
- nmap — port scanning and discovery
    
- ethtool — inspect NIC settings
    
- iptraf-ng — real‑time network monitoring