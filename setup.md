# ⚙️ Wazuh Setup Guide

This document covers how to set up the Wazuh server, install Wazuh on Ubuntu, and connect the Kali agent.

## 🖥️ Step 0 – Ubuntu Preparation

Before installing Wazuh, make sure your Ubuntu server is updated and has the required dependencies installed.

Run the following commands:
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl apt-transport-https lsb-release gnupg2 -y
```
📸 Screenshot

## 🛠️ Step 1 – Wazuh Deployment (Server Side)

Run the following on your Ubuntu Wazuh server:
```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash ./wazuh-install.sh -a
```
![Wazuh Installed](../screenshots/setup.md/wazuh-installed.png)

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
![Wazuh Agent Kali Installed](../screenshots/setup.md/wazuh-agent-kali-installed.png)  

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

📸 Screenshot: agent-status.png
