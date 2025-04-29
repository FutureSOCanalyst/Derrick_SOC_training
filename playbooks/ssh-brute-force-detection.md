

# 🛡️ SOC Playbook: SSH Brute Force Detection & Response

**Playbook ID:** PB-SSH-001  
**Analyst Level:** Tier 1  
**Created by:** Derrick Wilson  
**Last Updated:** April 29, 2025  

---

## 🧠 Objective

To detect and respond to brute-force SSH login attempts. These attacks involve an unauthorized actor making rapid and repeated login attempts in an effort to guess user credentials. This playbook helps Tier 1 analysts confirm the activity, document findings, and take appropriate action.

---

## 🚨 Trigger Conditions

The following should trigger this playbook:

- 5 or more failed SSH login attempts from the **same IP address** within a short timeframe (e.g., 5 minutes)  
- An alert from a SIEM or log monitoring system indicating suspicious SSH activity  
- Unusual login activity targeting **multiple usernames** such as `root`, `admin`, or local users  

---

## 🔍 Investigation Steps

These steps guide you through confirming the brute-force activity using system logs.

1. **Verify that SSH is active on the system:**

   sudo systemctl status ssh
   
Search for failed login attempts:
sudo journalctl -u ssh | grep "Failed"

Check for any successful logins following the failures:
sudo journalctl -u ssh | grep "Accepted"

Identify attacker behavior:
Look for the same source IP address repeated

Check if the same or multiple usernames were targeted

Note the number of attempts, and whether any succeeded

Determine if the system was accessed by an unauthorized user.

🛑 Containment Steps

Take immediate action to stop the intrusion and limit further risk:

Block the source IP (temporarily):

sudo iptables -A INPUT -s [attacker_ip] -j DROP

Lock the user account if compromise is suspected:
sudo usermod -L [username]

Alert the system owner or escalate to Tier 2/IR team.

🧾 Documentation Checklist

Make sure to record everything clearly:
 Create an incident ticket in your tracking system
 
 Save relevant log entries as evidence
 
 Record the source IP, usernames targeted, and timestamps
 
 Note whether any logins were successful
 
 Document severity level and rationale
 
 List any containment actions taken
 
 Write an incident summary in plain, professional language
 
✅ Recommended Follow-Up Actions

After containment, suggest preventive and hardening actions:

Enable fail2ban or a similar tool to automatically block brute-force attempts

Enforce key-based authentication instead of passwords

Require multi-factor authentication (MFA/2FA)

Review and rotate credentials for any affected users

Audit logs over the next 24–72 hours for continued attempts

🧪 Lab-tested by Derrick Wilson using Kali Linux, Hydra (for brute-force simulation), and system log analysis with journalctl.
