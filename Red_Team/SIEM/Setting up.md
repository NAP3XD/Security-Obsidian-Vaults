1. Requirements: Comprehend the purpose or necessity of the use case, pinpointing the specific scenario for which an alert or notification is needed. Requirements can be proposed by customers, analysts, or employees. For instance, the goal might be to design a detection use case for a brute force attack that triggers an alert after 10 consecutive login failures within 4 minutes.  
      
    
2. Data Points: Identify all data points within the network where a user account can be used to log in. Gather information about the data sources that generate logs for unauthorized access attempts or login failures. For example, data might come from Windows machines, Linux machines, endpoints, servers, or applications. Ensure logs capture essential details like user, timestamp, source, destination, etc.  
      
    
3. Log Validation: Verify and validate the logs, ensuring they contain all crucial information such as user, timestamp, source, destination, machine name, and application name. Confirm all logs are received during various user authentication events for critical data points, including local, web-based, application, VPN, and OWA (Outlook) authentication.  
      
    
4. Design and Implementation: After identifying and verifying all logs with different data points and sources, begin designing the use case by defining the conditions under which an alert should be triggered. Consider three primary parameters: Condition, Aggregation, and Priority. For example, in a brute force attack use case, create an alert for 10 login failures in 4 minutes while considering aggregation to avoid false positives and setting alert priority based on the targeted user's privileges.  
      
    
5. Documentation: Standard Operating Procedures (SOP) detail the standard processes analysts must follow when working on alerts. This includes conditions, aggregations, priorities, and information about other teams to which analysts need to report activities. The SOP also contains the escalation matrix.  
      
    
6. Onboarding: Start with the development stage before moving the alert directly into the production environment. Identify and address any gaps to reduce false positives, then proceed to production.  
      
    
7. Periodic Update/Fine-tuning: Obtain regular feedback from analysts and maintain up-to-date correlation rules by whitelisting. Continually refine and optimize the use case to ensure its effectiveness and accuracy.  
      
    

## How To Build SIEM Use Cases

- Comprehend your needs, risks, and establish alerts for monitoring all necessary systems accordingly.  
      
    
- Determine the priority and impact, then map the alert to the kill chain or MITRE framework.  
      
    
- Establish the Time to Detection (TTD) and Time to Response (TTR) for the alert to assess the SIEM's effectiveness and analysts' performance.  
      
    
- Create a Standard Operating Procedure (SOP) for managing alerts.  
      
    
- Outline the process for refining alerts based on SIEM monitoring.  
      
    
- Develop an Incident Response Plan (IRP) to address true positive incidents.  
      
    
- Set Service Level Agreements (SLAs) and Operational Level Agreements (OLAs) between teams for handling alerts and following the IRP.  
      
    
- Implement and maintain an audit process for managing alerts and incident reporting by analysts.  
      
    
- Create documentation to review the logging status of machines or systems, the basis for creating alerts, and their triggering frequency.  
      
    
- Establish a knowledge base document for essential information and updates to case management tools.  
      
    

When creating an SOP and documenting alert handling, consider the following:

- process.name
    
- process.parent.name
    
- event.action
    
- machine where the alert was detected
    
- user associated with the machine
    
- user activity within +/- 2 days of the alert's generation
    
- After gathering this information, defenders should engage with the user and examine the user's machine to analyze system logs, antivirus logs, and proxy logs from the SIEM for full visibility.