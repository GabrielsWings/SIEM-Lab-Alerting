# 🛡️ SIEM Lab – Wazuh + Kali + Metasploitable2

This project expands my network reconnaissance lab into a basic **Security Operations Center (SOC) simulation** by deploying a Wazuh SIEM server and forwarding logs from Kali Linux and Metasploitable2. The goal of this lab is to detect and triage malicious activity (failed SSH logins / brute-force attempts) in a safe, isolated environment.

---

## ⚙️ Lab Architecture
```bash
[Host Machine]
│
├── Kali Linux (Attacker) – <KALI_IP>
├── Metasploitable2 (Target) – <TARGET_IP>
└── Wazuh Server (SIEM) – <WAZUH_IP>
```
**Network Type:** Host-Only (fully isolated from Internet)

---

## ✅ Objectives

- Deploy a functional SIEM (Wazuh) in an isolated lab  
- Install and register endpoint agents on Kali and Metasploitable2  
- Simulate an attack (SSH brute-force)  
- Detect and triage the event in Wazuh

---

## 🛠️ Step 1 – Wazuh Deployment

```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash ./wazuh-install.sh -a
```
📸 Screenshot: wazuh-install-finished.png

## 🛠️ Step 2 – Agent Installation (Kali and Metasploitable2)
```bash
curl -sO https://packages.wazuh.com/4.x/apt/wazuh-agent_4.7.0-1_amd64.deb
sudo dpkg -i wazuh-agent_4.7.0-1_amd64.deb
sudo nano /var/ossec/etc/ossec.conf   <-- change <address> to <WAZUH_IP>
sudo systemctl enable --now wazuh-agent
```
📸 Screenshot: agent-connected.png

## 🔥 Step 3 – Simulated Attack
```bash
hydra -l msfadmin -P /usr/share/wordlists/rockyou.txt ssh://<TARGET_IP>
```
⬇
## 👁️ Step 4 – Detection / Alerting (Wazuh)
```bash
Open https://<WAZUH_IP>:5601

Go to Security → Events

Filter by source.ip = <KALI_IP>
```
📸 Screenshot: ssh-alert.png

## 📝 Summary / Takeaways
Stage	Result

Wazuh Deployment	✅ SIEM installed successfully

Agent Registration	✅ Kali & Metasploitable2 agents connected

Simulated Attack	✅ SSH brute-force generated

Alert Detected	✅ Wazuh generated alert and displayed source, IP, and event details
