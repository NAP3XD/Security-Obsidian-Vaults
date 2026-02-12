[Confirmed DLL Candidates][https://www.wietzebeukema.nl/blog/hijacking-dlls-in-windows]


### CRL.DLL
#powershell #crlDOTdll

```
ImageLoaded: C:\Windows\System32\crl.dll
```

This usually means the process is doing **certificate validation**.

Common processes that load it:

- `svchost.exe`
- `powershell.exe`
- `CHXSmartScreen.exe`
- `msedge.exe` / `chrome.exe`
- `lsass.exe`
- `wininit.exe`
Event 7: Module load events 

## IOCs
Let's explore these IOCs:

1. "calc.exe", originally located in System32, should not be found in a writable directory. Therefore, a copy of "calc.exe" in a writable directory serves as an IOC, as it should always reside in System32 or potentially Syswow64.
    
2. "WININET.dll", originally located in System32, should not be loaded outside of System32 by calc.exe. If instances of "WININET.dll" loading occur outside of System32 with "calc.exe" as the parent process, it indicates a DLL hijack within calc.exe. While caution is necessary when alerting on all instances of "WININET.dll" loading outside of System32 (as some applications may package specific DLL versions for stability), in the case of "calc.exe", we can confidently assert a hijack due to the DLL's unchanging name, which attackers cannot modify to evade detection.
    
3. The original "WININET.dll" is Microsoft-signed, while our injected DLL remains unsigned.
    

These three powerful IOCs provide an effective means of detecting a DLL hijack involving calc.exe. It's important to note that while Sysmon and event logs offer valuable telemetry for hunting and creating alert rules, they are not the sole sources of information.