## Tools
### RDP
```shell-session
xfreerdp /u:Administrator /p:'[password]' /v:[Target IP] /dynamic-resolution
```
#RDP 
### SMB
```
smbclient -L //SERVER_NAME -U username

smbclient //SERVER_NAME/SHARE -U username

sudo apt install -y cifs-utils

sudo mount -t cifs //SERVER_NAME/SHARE /mount/here -o username=USERNAME
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
```

### Venv

#### linux
Python3 -m venv [name of env “python_env, venv]

Source ./python_env/bin/activate
Deactivate

#### Win
win_venv/Scripts/activate.bat

### SSh-Keygen
#key
ssh-keygen -t ed25519 -C "your_email@example.com"

## Debug

### Port testing
#ss
sudo ss -tnlp | grep postgres       // find port service running on



  

## Web server Hosting
#php 
php -S localhost:8000

Python3 -m http.server <port>