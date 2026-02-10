
`System Monitor (Sysmon)` is a Windows system service and device driver that remains resident across system reboots to monitor and log system activity to the Windows event log. Sysmon provides detailed information about process creation, network connections, changes to file creation time, and more.

With the modified Sysmon configuration, we can start observing image load events. To view these events, navigate to the Event Viewer and access "Applications and Services" -> "Microsoft" -> "Windows" -> "Sysmon." A quick check will reveal the presence of the targeted event ID.

### Config 
Reload Sysmon config 
```cmd-session
C:\Tools\Sysmon> sysmon.exe -c sysmonconfig-export.xml
```

- For a comprehensive configuration, we can visit: [https://github.com/SwiftOnSecurity/sysmon-config](https://github.com/SwiftOnSecurity/sysmon-config). <-- `We will use this one in this section!`
- Another option is: [https://github.com/olafhartong/sysmon-modular](https://github.com/olafhartong/sysmon-modular), which provides a modular approach.
### Docs
https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon
Also common event IDs
### Sysmon 4 Linux
[Sysmon4Linux][https://github.com/microsoft/SysmonForLinux]

### Process Hacker
https://systeminformer.sourceforge.io/