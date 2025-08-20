# ⚙️ Wazuh Setup Guide

This document covers how to set up the Wazuh server, install Wazuh on Ubuntu, and connect the Kali agent.

## 🖥️ Step 0 – Ubuntu Preparation

Before installing Wazuh, make sure your Ubuntu server is updated and has the required dependencies installed.

Run the following commands:
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl apt-transport-https lsb-release gnupg2 -y
```
## 🛠️ Step 1 – Wazuh Deployment (Server Side)

Run the following on your Ubuntu Wazuh server:
```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash ./wazuh-install.sh -a
```
<img width="815" height="575" alt="Wazuh Installed" src="https://github.com/user-attachments/assets/ea441d0d-5099-4042-96e7-abb6f34b7c44" />

## 🖥️ Step 2 – Kali Agent Installation

Run the following on your Kali Linux VM:
```bash
curl -sO https://packages.wazuh.com/4.x/apt/wazuh-agent_4.8.2-1_amd64.deb
sudo dpkg -i wazuh-agent_4.8.2-1_amd64.deb
```
Edit the agent configuration file:
```bash
sudo nano /var/ossec/etc/ossec.conf
```
➡️ Update the <address> field with your Wazuh server IP.

Then enable and start the agent:
```bash
sudo systemctl enable --now wazuh-agent
```
<img width="638" height="510" alt="Wazuh Agent Kali Installed" src="https://github.com/user-attachments/assets/f6b28f01-393e-45d3-821a-bbf8cea76763" />

## 🔄 Step 3 – Restart Services

To ensure everything is running properly:
```bash
sudo systemctl restart wazuh-manager   # on the server
sudo systemctl restart wazuh-agent     # on the Kali VM
```
## ✅ Step 4 – Verify Connection

Log into the Wazuh dashboard on the Ubuntu browser:
```bash
URL: https://<WAZUH_IP>
```
Navigate to: Agents → Agent status

Confirm your Kali VM agent shows up as Active.

<img width="1281" height="875" alt="Kali connected  to Wazuh" src="https://github.com/user-attachments/assets/19bdb8b4-438f-4dba-86ac-96c484ea4f88" />

