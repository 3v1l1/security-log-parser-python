# Security Log Parser (Python)

This project demonstrates basic automation of log analysis using Python.  
The script processes authentication logs to identify repeated failed login attempts from the same IP address.

---

## Objective

To simulate how a SOC analyst can use Python to automate the detection of suspicious activity in log files.

---

## Example Log Entry

Failed password for admin from 203.0.113.45 port 22 ssh2

---

## Script Functionality

- Reads log file line by line  
- Identifies failed login attempts  
- Extracts IP addresses  
- Counts repeated attempts from the same IP  

**Script file:** `log_parser.py`

---

## How to Run

1. Save the log file as `auth.log`  
2. Run the script:

```bash
python log_parser.py
failed_logins = {}

with open("auth.log") as file:
    for line in file:
        if "Failed password" in line and "from" in line:
            ip = line.split("from ")[1].split(" ")[0]
            if ip in failed_logins:
                failed_logins[ip] += 1
            else:
                failed_logins[ip] = 1

for ip, count in failed_logins.items():
    print(ip, count)
```
---
Example Output
203.0.113.45 3
198.51.100.10 1

---

## This script helps:

- Detect potential brute-force attacks  
- Identify suspicious IP activity  
- Reduce manual effort in log review  

---

## Tools / Concepts Used:

- Python
- Log Analysis  
- Security Monitoring
- Basic Automation  

---
