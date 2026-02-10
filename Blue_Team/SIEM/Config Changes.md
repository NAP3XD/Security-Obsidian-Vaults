In our specific use case, we aim to detect a DLL hijack. The Sysmon event log IDs relevant to DLL hijacks can be found in the Sysmon documentation ([https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon)). To detect a DLL hijack, we need to focus on `Event Type 7`, which corresponds to module load events. To achieve this, we need to modify the `sysmonconfig-export.xml` Sysmon configuration file we downloaded from [https://github.com/SwiftOnSecurity/sysmon-config](https://github.com/SwiftOnSecurity/sysmon-config).

By examining the modified configuration, we can observe that the "include" comment signifies events that should be included.

![XML snippet showing RuleGroup with ImageLoad set to 'include' and a note about no rules meaning nothing will be logged.](https://academy.hackthebox.com/storage/modules/216/image14.png)

In the case of detecting DLL hijacks, we change the "include" to "exclude" to ensure that nothing is excluded, allowing us to capture the necessary data.

![XML snippet with RuleGroup, ImageLoad set to 'exclude', and a note about using 'include' with no rules.](https://academy.hackthebox.com/storage/modules/216/image15.png)

To utilize the updated Sysmon configuration, execute the following.

```cmd-session
C:\Tools\Sysmon> sysmon.exe -c sysmonconfig-export.xml
```

With the modified Sysmon configuration, we can start observing image load events. To view these events, navigate to the Event Viewer and access "Applications and Services" -> "Microsoft" -> "Windows" -> "Sysmon." A quick check will reveal the presence of the targeted event ID.