OVERVIEW

This project explores the use of Microsoft Sentinel to identify and neutralize cyber threats originating from malicious scheduled tasks in Azure cloud environments. It highlights how attackers exploit legitimate automation tools (scheduled tasks) to maintain persistence, escalate privileges, and execute Advanced Persistent Threats (APTs). To address these risks, the I developed a Security Information and Event Management (SIEM) solution that establishes a behavioral baseline to distinguish between benign and harmful tasks. The framework utilizes Kusto Query Language (KQL) for detection and Azure Logic Apps to automate the isolation of compromised virtual machines. Ultimately, the study provides a structured methodology for enhancing cloud security infrastructure and reducing the impact of sophisticated data breaches. 

CONCEPTUAL FRAMEWORK

The SIEM solution created involved integrating Microsoft Sentinel with azure resources to 
improve on its SIEM capabilities, specifically targeting the detection and mitigation of threats 
associated with scheduled tasks. The framework involves the following process: 
First is scheduled task execution, where a scheduled task is executed on the Azure VM, 
generating a security event log. This is followed by log collection, the logs from the VM are 
collected and sent to azure log analytics workspace. Next is log analysis in azure sentinel, the 
collected logs are analysed using custom analytic rules and custom scripts to identify suspicious 
behaviour. A decision is then made, if the task is benign the system returns to log collected to 
determine if the other log events are benign or malicious, if no task was executed the system 
waits for tasks to be executed on the VM and if task is malicious the system moves to the fourth 
step. The fourth step is detection and alert generation, when Sentinel identifies a malicious 
task, its configured to generate an alert that triggers the response. The fifth step is the automated 
response: The alert triggers an automated response configured using the azure logic app tool 
which isolates the affected VM to mitigate the threat. 


<img width="528" height="320" alt="image" src="https://github.com/user-attachments/assets/2b625d50-ae59-4b23-95bd-37b18f84fb19" />
