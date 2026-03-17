# Security Log Parser (Python)

This project demonstrates basic automation of log analysis using Python.
The script processes authentication logs to identify repeated failed login attempts.

---

## Objective

To simulate how a SOC analyst can use Python to automate the detection of suspicious activity in log files.

---

## Example Log Entry


---

## Script Functionality

- Reads log file line by line
- Identifies failed login attempts
- Extracts IP addresses
- Counts repeated attempts from the same IP

---

## Sample Python Code

```python
failed_logins = {}

with open("auth.log") as file:
    for line in file:
        if "Failed password" in line:
            ip = line.split("from ")[1].split(" ")[0]
            if ip in failed_logins:
                failed_logins[ip] += 1
            else:
                failed_logins[ip] = 1

for ip, count in failed_logins.items():
    print(ip, count)
