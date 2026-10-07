Windows Event Log Security Analyzer

A Python-based security monitoring tool that parses Windows Event Log (.evtx) exports, identifies authentication-related security events, detects account lockouts, and generates a comprehensive summary report for security analysis and incident investigation.

Features
Read and parse Windows Event Log (.evtx) files
Detect failed login attempts
Detect account lockout events
Extract relevant security information:
Username
Timestamp
Source IP address (when available)
Event ID
Generate summary reports
Calculate security statistics
Export findings to CSV and text reports
Support multiple .evtx files
Security Events Monitored
Event ID	Description4625	Failed Login Attempt
4740	Account Locked Out
4624	Successful Login (Optional)
4634	User Logoff (Optional)
Project Structure
maincode101/
│
─ main.py
─ parser.py
─ detector.py
─ reporter.py
─ requirements.txt
├── README.md
│
├── input/
│   └── security.evtx
│
├── reports/
│   ├── summary_report.txt
│   └── findings.csv
│
└── logs/

Requirements
Python 3.9+
Windows Event Log export files (.evtx)
Python Libraries
pip install python-evtx pandas tabulate


Or install from requirements.txt:

pip install -r requirements.txt

Usage
Run the Analyzer
python main.py input/security.evtx

Analyze Multiple Files
python main.py input/

Example Output
Console Summary
=================================
Windows Security Event Analysis
=================================

Failed Login Attempts: 153
Account Lockouts: 12

Top Targeted Accounts:
---------------------------------
administrator : 78
jsmith        : 42
guest         : 33

Analysis Complete.

CSV Report
Timestamp,EventID,User,SourceIP,Description
2025-01-10 08:45:16,4625,administrator,192.168.1.10,Failed Login
2025-01-10 08:48:22,4740,administrator,N/A,Account Lockout

How It Works
Reads one or more .evtx files.
Parses the XML records contained in the event logs.
Filters authentication-related security events.
Identifies:
Failed login attempts (Event ID 4625)
Account lockouts (Event ID 4740)
Aggregates findings.
Generates summary reports and statistics.
Use Cases
Security Operations Center (SOC) monitoring
Incident response investigations
Brute-force attack detection
Audit and compliance reporting
User account activity analysis
Threat hunting
Example Report Metrics

The generated report includes:

Total failed logins
Total account lockouts
Most targeted accounts
Most active source IPs
Event timeline
Lockout frequency
Security recommendations
Future Enhancements
Real-time monitoring
SIEM integration
Email alerts
Dashboard visualization
Geolocation lookup for source IPs
Detection of password spraying attacks
Detection of brute-force attacks
PDF report generation
Author

Developed as a security analysis tool for Windows authentication event monitoring and investigation.

License

This project is released under the MIT License. Feel free to use, modify, and distribute it.
