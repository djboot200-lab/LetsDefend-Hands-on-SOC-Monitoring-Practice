# LetsDefend-Hands-on-SOC-Monitoring-Practice
🛡️ SOC Alert Triage & Investigation Portfolio
LetsDefend — Hands-on SOC Monitoring Practice
This repository documents my hands-on practice in SOC alert triage, security event investigation, vulnerability analysis, malware detection, phishing analysis, IOC investigation, and MITRE ATT&CK mapping using the LetsDefend SOC Monitoring environment.
The objective of these investigations is to develop a practical SOC L1 Analyst workflow:
Alert
  ↓
Initial Triage
  ↓
Alert Validation
  ↓
IOC Investigation
  ↓
Log / Event Analysis
  ↓
Attack Context
  ↓
MITRE ATT&CK Mapping
  ↓
Verdict
  ↓
Response Recommendation
  ↓
Documentation
________________________________________
📊 Investigation Summary
#	Severity	Event ID	Detection / Rule	Alert Type
01	Medium	76	SOC137 — Malicious File/Script Download Attempt	Malware
02	Critical	320	SOC342 — CVE-2025-53770 SharePoint ToolShell Auth Bypass and RCE	Web Attack
03	Critical	316	SOC338 — Lumma Stealer — DLL Side-Loading via Click Fix Phishing	Data Leakage
04	Critical	314	SOC336 — Windows OLE Zero-Click RCE Exploitation Detected (CVE-2025-21298)	Malware
05	Medium	313	SOC335 — CVE-2024-49138 Exploitation Detected	Privilege Escalation
________________________________________
🔎 Case 01 — Malicious File/Script Download Attempt
Rule: SOC137
Event ID: 76
Severity: Medium
Category: Malware
Investigation Focus
•	Identify the source of the download
•	Identify the affected endpoint
•	Determine downloaded file/script
•	Analyze file hash and reputation
•	Investigate user and process activity
•	Identify any subsequent execution
•	Check for network communication
•	Determine whether the activity was malicious or benign
Investigation Workflow
Download Attempt
      ↓
Source Identification
      ↓
File / Script Analysis
      ↓
Hash / IOC Investigation
      ↓
Process Correlation
      ↓
Network Analysis
      ↓
Verdict
Evidence
•	Source:
•	Destination Host:
•	Username:
•	Filename:
•	File Hash:
•	URL / Domain:
•	Process:
•	Parent Process:
•	Network Activity:
MITRE ATT&CK
To be mapped based on the observed behavior and evidence.
Analyst Verdict
Pending investigation
Recommended Response
Depending on findings:
•	Isolate affected endpoint if compromise is suspected
•	Block malicious URL/domain/hash
•	Remove malicious artifact
•	Hunt for the IOC across the environment
•	Review subsequent process execution
•	Monitor the affected endpoint
________________________________________
🚨 Case 02 — CVE-2025-53770 SharePoint ToolShell Auth Bypass & RCE
Rule: SOC342
Event ID: 320
Severity: Critical
Category: Web Attack
Investigation Focus
•	Identify targeted SharePoint server
•	Determine source IP
•	Investigate HTTP request patterns
•	Identify authentication bypass indicators
•	Search for exploitation attempts
•	Investigate possible command execution
•	Look for web shells or newly created files
•	Review outbound connections
•	Determine whether exploitation succeeded
Investigation Workflow
Incoming Web Request
        ↓
Source IP
        ↓
HTTP Request Analysis
        ↓
Authentication Bypass Indicator
        ↓
RCE Evidence
        ↓
Process / File Activity
        ↓
Network Connection
        ↓
Scope Assessment
Evidence
•	Source IP:
•	Destination Server:
•	URI / Endpoint:
•	HTTP Method:
•	User-Agent:
•	Status Code:
•	Request Pattern:
•	Process Created:
•	File Created:
•	Outbound Connection:
MITRE ATT&CK
Map techniques according to confirmed post-exploitation behavior.
Potential areas to investigate:
•	Initial Access
•	Exploitation for Client Execution / Exploitation of Public-Facing Application
•	Command and Scripting Interpreter
•	Web Shell / Server Software Component
•	Command & Control
Analyst Verdict
Pending investigation
Recommended Response
•	Restrict or isolate affected SharePoint server if exploitation is confirmed
•	Preserve relevant web/server logs
•	Identify and remove malicious artifacts
•	Hunt for the source IOC across the environment
•	Patch the affected software
•	Review authentication and privileged activity
•	Investigate possible lateral movement
________________________________________
🦠 Case 03 — Lumma Stealer / DLL Side-Loading / ClickFix Phishing
Rule: SOC338
Event ID: 316
Severity: Critical
Category: Data Leakage
Investigation Focus
•	Investigate phishing delivery mechanism
•	Identify affected user and endpoint
•	Identify malicious payload
•	Investigate DLL side-loading behavior
•	Analyze process parent-child relationships
•	Search for credential/data theft indicators
•	Investigate outbound C2 communication
•	Identify additional affected hosts/users
Investigation Workflow
ClickFix / Phishing
       ↓
User Interaction
       ↓
Payload Execution
       ↓
DLL Side-Loading
       ↓
Lumma Stealer Activity
       ↓
Credential / Data Access
       ↓
C2 Communication
       ↓
Containment
Evidence
•	Sender:
•	Recipient:
•	Email Subject:
•	URL:
•	Attachment:
•	Filename:
•	SHA-256:
•	Parent Process:
•	Child Process:
•	DLL:
•	Destination IP/Domain:
•	User:
MITRE ATT&CK
Map confirmed behavior to relevant techniques such as:
•	Phishing
•	User Execution
•	Command and Scripting Interpreter
•	DLL Side-Loading
•	Credentials from Web Browsers
•	Application Layer Protocol
Final technique mapping should be based on evidence rather than the alert name alone.
Analyst Verdict
Pending investigation
Recommended Response
•	Isolate affected endpoint
•	Block identified malicious infrastructure
•	Preserve forensic evidence
•	Reset potentially compromised credentials
•	Investigate browser/session credential exposure
•	Hunt for the same payload and IOC across endpoints
•	Check for persistence and lateral movement
________________________________________
💥 Case 04 — CVE-2025-21298 Windows OLE RCE
Rule: SOC336
Event ID: 314
Severity: Critical
Category: Malware
Investigation Focus
•	Identify affected Windows endpoint
•	Investigate malicious RTF/email attachment
•	Validate vulnerability/patch status
•	Investigate Office/OLE-related activity
•	Review process creation
•	Investigate PowerShell/cmd activity
•	Review Sysmon network events
•	Search for dropped files
•	Investigate possible persistence
•	Determine whether exploitation was successful
Investigation Workflow
Malicious Attachment
        ↓
RTF / OLE Processing
        ↓
Potential Exploitation
        ↓
Process Creation
        ↓
PowerShell / Command Execution
        ↓
File Creation
        ↓
DNS / Network Activity
        ↓
Persistence / C2
Evidence
•	Sender:
•	Recipient:
•	Subject:
•	Attachment:
•	SHA-256:
•	Source IP:
•	Hostname:
•	Username:
•	Process:
•	Parent Process:
•	Command Line:
•	Destination IP/Domain:
•	DNS Query:
MITRE ATT&CK
Potential mappings depend on observed behavior:
•	T1566.001 — Spearphishing Attachment
•	T1059.001 — PowerShell
•	T1059.003 — Windows Command Shell
•	Other techniques only when supported by evidence.
Analyst Verdict
Pending investigation
Recommended Response
If exploitation is confirmed or strongly suspected:
1.	Isolate affected endpoint
2.	Preserve Windows/Sysmon/email evidence
3.	Identify affected users and hosts
4.	Hunt the attachment hash and related IOCs
5.	Investigate process and network activity
6.	Remove malicious artifacts/persistence
7.	Apply required security updates
8.	Reset compromised credentials where appropriate
9.	Continue post-containment monitoring
________________________________________
⚠️ Case 05 — CVE-2024-49138 Exploitation Detected
Rule: SOC335
Event ID: 313
Severity: Medium
Category: Privilege Escalation
Investigation Focus
•	Identify affected endpoint/server
•	Determine exploitation source
•	Review Windows security events
•	Investigate process creation
•	Identify privilege changes
•	Investigate suspicious account activity
•	Correlate process, authentication and network events
•	Determine whether privilege escalation occurred
Investigation Workflow
Exploit Attempt
      ↓
Affected Host
      ↓
Process / Security Events
      ↓
Privilege Change
      ↓
Account Activity
      ↓
Post-Exploitation Activity
      ↓
Scope Assessment
Evidence
•	Source IP:
•	Destination Host:
•	Username:
•	Process:
•	Parent Process:
•	Event IDs:
•	Privilege Change:
•	New Account / Token:
•	Network Activity:
•	Related IOC:
MITRE ATT&CK
Map according to the observed exploitation and subsequent behavior.
Potential investigation areas:
•	Privilege Escalation
•	Exploitation for Privilege Escalation
•	Valid Accounts
•	Command and Scripting Interpreter
•	Persistence
Analyst Verdict
Pending investigation
Recommended Response
•	Investigate the affected endpoint immediately
•	Preserve relevant event logs
•	Identify newly elevated accounts/processes
•	Hunt for related IOCs
•	Remove unauthorized persistence
•	Patch the vulnerable system
•	Review privileged account activity
•	Monitor for lateral movement
________________________________________
🧠 Common SOC Investigation Methodology
Across these investigations, I am practicing the following SOC workflow:
1. Alert Triage
What happened?
Where did it happen?
When did it happen?
Who was affected?
Why did the detection trigger?
2. Evidence Collection
Host
User
IP
Domain
URL
Hash
Filename
Process
Command Line
Parent Process
Event ID
Timestamp
3. Correlation
Correlate:
Email
+
Windows Events
+
Sysmon
+
Process Activity
+
DNS
+
Network Connections
+
Authentication
4. IOC Investigation
Investigate:
•	IP addresses
•	Domains
•	URLs
•	File hashes
•	Filenames
•	Process names
•	Command lines
•	Email addresses
•	Malicious attachments
5. MITRE ATT&CK Mapping
Map observed attacker behavior to the appropriate:
Tactic
   ↓
Technique
   ↓
Sub-technique
6. Verdict
Possible outcomes:
True Positive
False Positive
Benign True Positive
Suspicious / Requires Escalation
The final verdict should be based on evidence collected during the investigation.
________________________________________
📚 Skills Practiced
SOC Operations
•	Alert Triage
•	Alert Validation
•	Incident Prioritization
•	Escalation
•	Incident Documentation
Threat Detection
•	Malware Detection
•	Phishing Detection
•	Exploitation Detection
•	Network Attack Detection
•	Privilege Escalation Detection
Investigation
•	IOC Analysis
•	Windows Event Log Analysis
•	Sysmon Analysis
•	Process Analysis
•	Network Investigation
•	Email Investigation
•	Timeline Analysis
Frameworks
•	MITRE ATT&CK
•	IOC-based Detection
•	Behavior-based Detection
Incident Response
•	Containment
•	Evidence Preservation
•	Eradication
•	Recovery
•	Threat Hunting
•	Post-Incident Monitoring
________________________________________
🎯 Learning Objective
The goal of this project is to develop practical skills required for a SOC L1 / Junior Security Analyst role and progressively build toward advanced DFIR, Threat Hunting and Detection Engineering capabilities.
My focus is not only on identifying an alert, but understanding:
What happened → How it happened → What was affected → What evidence proves it → What the attacker did next → How the incident should be contained and investigated.
________________________________________
⚠️ Disclaimer
This repository documents cybersecurity training and hands-on learning activities performed in authorized training environments.
Training-platform proprietary content, credentials, sensitive information and unnecessary challenge-specific answers are not reproduced. Investigation notes are my own learning documentation and analysis.
________________________________________
🛠️ Tools & Technologies
LetsDefend
SIEM
Windows Event Logs
Sysmon
MITRE ATT&CK
IOC Analysis
Threat Intelligence
Network Analysis
Incident Response
DFIR
Threat Hunting
________________________________________
📈 Progress
SOC Alert Triage
████████████████████████░░  5+ Investigations

IOC Analysis
██████████████████░░░░░░░░  In Progress

Windows/Sysmon Investigation
████████████████░░░░░░░░░░  In Progress

MITRE ATT&CK
██████████████░░░░░░░░░░░░  In Progress

Incident Response
████████████░░░░░░░░░░░░░░  Developing
Next: Continue building hands-on SOC investigations, SIEM detections, Windows telemetry analysis, DFIR skills, threat hunting and detection engineering.

