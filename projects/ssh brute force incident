 INCIDENT: SSH Brute Force Attempt (Simulated)

Date: April 29, 2025
Detected by: Analyst-in-training (Derrick Wilson)
Log Source: journalctl -u ssh

 Summary:
A simulated brute-force login attack was conducted against the local SSH service on localhost. The attacker attempted 9 password guesses using the derrickwilson username in order to gain unauthorized access. The activity was conducted locally using the hydra tool to test detection capabilities.

 Observations:
Number of attempts: 9


Failed attempts: 9

Successful logins: 0 

Username targeted: derrickwilson

Source IP	::1 (localhost)

Tool Used: hydra

Analyst Notes:
The pattern of repeated SSH login attempts with multiple common passwords is consistent with a brute-force attack. Since all traffic originated from the local machine (::1), and the activity was intentionally simulated, no real compromise occurred.

In a real environment, this type of behavior should trigger automated alerts and may indicate an attacker or a misconfigured script.

Recommendations:
Monitor SSH for excessive failed login attempts

Implement IP-based lockouts or fail2ban

Enforce key-based authentication where possible

Configure alerts for >5 failed login attempts in a short time period

Review system access logs regularly


Note: This incident was simulated in a controlled lab environment as part of my SOC Analyst training. No actual system was compromised.
