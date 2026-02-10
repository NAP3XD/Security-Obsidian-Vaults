[WIN_Audit_Event_EventCodes][The `Keywords` field is particularly useful when filtering event logs for specific types of events. It can significantly enhance the precision of search queries by allowing us to specify events of interest, thus making log management more efficient and effective.]

## Tips
use 'Find' to search for a string match 

Event Viewer or Windows Event Log API
## Log Types and Components

The default Windows event logs consist of `Application`, `Security`, `Setup`, `System`, and `Forwarded Events`.

It should be noted, that the Windows Event Viewer has the ability to open and display previously saved `.evtx` files, which can be then found in the "Saved Logs" section.

When examining `Application` logs, we encounter two distinct levels of events: `information` and `error`.

Each entry in the Windows Event Log is an "Event" and contains the following primary components:

1. `Log Name`: The name of the event log (e.g., Application, System, Security, etc.).
2. `Source`: The software that logged the event.
3. `Event ID`: A unique identifier for the event.
4. `Task Category`: This often contains a value or name that can help us understand the purpose or use of the event.
5. `Level`: The severity of the event (Information, Warning, Error, Critical, and Verbose).
6. `Keywords`: Keywords are flags that allow us to categorize events in ways beyond the other classification options. These are generally broad categories, such as "Audit Success" or "Audit Failure" in the Security log.
7. `User`: The user account that was logged on when the event occurred.
8. `OpCode`: This field can identify the specific operation that the event reports.
9. `Logged`: The date and time when the event was logged.
10. `Computer`: The name of the computer where the event occurred.
11. `XML Data`: All the above information is also included in an XML format along with additional event data.


The `Keywords` field is particularly useful when filtering event logs for specific types of events. It can significantly enhance the precision of search queries by allowing us to specify events of interest, thus making log management more efficient and effective.

### Leveraging Custom XML Queries
[Adv_XML_Filtering][https://techcommunity.microsoft.com/blog/askds/advanced-xml-filtering-in-the-windows-event-viewer/399761]

To streamline our analysis, we can create custom XML queries to identify related events using the "Logon ID" as a starting point. By navigating to "Filter Current Log" -> "XML" -> "Edit Query Manually," we gain access to a custom XML query language that enables more granular log searches.