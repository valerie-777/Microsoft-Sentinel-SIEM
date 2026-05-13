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

EXECUTION 

The outcome of the functional and non-functional testing show that the SIEM solution was 
successful in accurately detecting and responding to scheduled task-based threats in a cloud 
environment.  
According to the functional requirements, the system was able to collect all security event logs 
from the virtual machine. Specific KQL queries enabled categorization of the logs to find which 
tasks created by a specific user and more details or metadata about the tasks as seen below. 

<img width="469" height="211" alt="image" src="https://github.com/user-attachments/assets/ce398254-1237-4d8d-90ca-0ff3424647b5" />

The system distinguished between a benign and malicious task reliably. When a malicious task 
is executed, the alert set by the analytic rule discussed in system implementation is triggered 
as seen below (red).

<img width="476" height="219" alt="image" src="https://github.com/user-attachments/assets/dee03761-a596-4284-8a26-dd2bb22e89ef" /> 

The system was able to detect the malicious task executed and the alerts created triggered 
automated response.  

<img width="504" height="167" alt="image" src="https://github.com/user-attachments/assets/2ef74943-d0a4-4a26-a03b-36f52ec02e39" /> 

The detection of the malicious task triggered the automated response (playbook) using azure 
logic apps which isolated the compromised VM in real time within minutes of detecting the 
malicious task executed in the virtual machine, thus fulfilling its nonfunctional requirements. 
This can be seen below in the time when the alert was generated, and the email was sent to the 
administrator.

<img width="473" height="237" alt="image" src="https://github.com/user-attachments/assets/b333c230-ebd9-410c-bc8b-467f71c8e49c" /> 

<img width="487" height="268" alt="image" src="https://github.com/user-attachments/assets/3de60cdc-ca9c-4f6c-a511-072c44b20164" /> 

In conclusion the SIEM was able to detect the malicious scheduled task in the virtual machine 
and mitigate it by isolating the virtual machine to avoid further compromise to other machines 
in the cloud network. 




