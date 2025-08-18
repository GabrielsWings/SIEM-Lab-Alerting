# 🔎 SIEM Analysis – SSH Bruteforce Detection

**Target:** Metasploitable2 (192.168.56.103)  

**Attacker:** Kali Linux (192.168.56.101)  

**SIEM:** Wazuh All-In-One

---

## 🎯 Objective

Simulate a malicious activity (SSH brute-force attack) and verify that the Wazuh SIEM is able to **capture**, **analyze**, and **generate an alert** for that activity.

---

## 🛠️ Attack Command (Run from Kali)

```bash
hydra -l msfadmin -P /usr/share/wordlists/rockyou.txt ssh://192.168.56.103
```
📸 Screenshot:

## 📝 Notes / Analysis
Item	Result

Attack Detected	✅ Yes

Alert Type	SSH Authentication Failure / Brute-Force

Source IP	192.168.56.101 (Kali)

Destination IP	192.168.56.103 (Metasploitable2)

Log Source	Wazuh Agent on Metasploitable2

### Summary:
Wazuh successfully detected multiple failed SSH authentication attempts coming from the Kali machine.
This proves that agent log forwarding, alert parsing, and SIEM event visualization are working correctly in the lab environment.
