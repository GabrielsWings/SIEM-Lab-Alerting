# ⚙️ Wazuh Setup Guide

This document covers how to set up the Wazuh server, install Wazuh on Ubuntu, and connect the Kali agent.

## 🖥️ Step 0 – Ubuntu Preparation

Before installing Wazuh, make sure your Ubuntu server is updated and has the required dependencies installed.

Run the following commands:

sudo apt update && sudo apt upgrade -y
sudo apt install curl apt-transport-https lsb-release gnupg2 -y


📸 Screenshot: ubuntu-updated.png

🛠️ Step 1 – Wazuh Deployment (Server Side)

Run the following on your Ubuntu Wazuh server:

curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash ./wazuh-install.sh -a


📸 Screenshot: wazuh-install-finished.png

🖥️ Step 2 – Kali Agent Installation

Run the following on your Kali Linux VM:

curl -sO https://packages.wazuh.com/4.x/apt/wazuh-agent_4.8.2-1_amd64.deb
sudo dpkg -i wazuh-agent_4.8.2-1_amd64.deb


Edit the agent configuration file:

sudo nano /var/ossec/etc/ossec.conf


➡️ Update the <address> field with your Wazuh server IP.

Then enable and start the agent:

sudo systemctl enable --now wazuh-agent


📸 Screenshot: kali-agent-installed.png

🔄 Step 3 – Restart Services

To ensure everything is running properly:

sudo systemctl restart wazuh-manager   # on the server
sudo systemctl restart wazuh-agent     # on the Kali VM

✅ Step 4 – Verify Connection

Log into the Wazuh dashboard:

URL: https://<WAZUH_IP>:5601

Navigate to: Agents → Agent status

Confirm your Kali VM agent shows up as Active.

📸 Screenshot: agent-status.png
