# 🛡️ SIEM Lab – Wazuh + Kali  

This project demonstrates a basic **Security Operations Center (SOC) simulation** using **Wazuh** as a SIEM server and **Kali Linux** as a monitored endpoint. The lab shows how to deploy Wazuh, register an agent, generate logs, and view events and compliance alerts in the Wazuh dashboard.  

---

## ⚙️ Lab Architecture  

```bash
[Host Machine]
│
├── Kali Linux (Agent) – <197.168.56.101>
└── Wazuh Server (SIEM) – <197.168.56.107>
```

Network Type: Host-Only (isolated from the Internet)

## ✅ Objectives

Deploy a functional SIEM (Wazuh) in an isolated lab

Install and register the Kali Linux agent

Generate system and authentication logs from Kali

Detect and analyze events in the Wazuh dashboard

View compliance reporting for frameworks such as GDPR and HIPAA

## 📂 Repository Structure
```bash
SIEM-Lab/
│
├── README.md              # Project overview (this file)
├── setup/                 # Wazuh + Kali installation steps
│   ├── setup.md
│   └── screenshots/
│
└── logs/                  # Log generation & detection steps
    ├── logs.md
    └── screenshots/
```

## 🚀 Setup
Instructions for installing Wazuh and registering the Kali agent are documented in the setup folder.

## 🔥 Log Generation & Detection
Steps to generate logs on Kali and view them in the Wazuh dashboard are documented in the logs folder.

## 📝 Summary / Results

Wazuh Deployment	✅ SIEM installed successfully

Agent Registration	✅ Kali agent connected and active

Log Generation	✅ System and authentication events created on Kali

Event Detection	✅ Wazuh received, parsed, and displayed events in the dashboard

Compliance Reporting ✅ Events mapped to compliance frameworks (e.g., GDPR, HIPAA)

## 📸 Screenshots

Screenshots of each stage are included in the respective folders:

setup/screenshots

logs/screenshots
