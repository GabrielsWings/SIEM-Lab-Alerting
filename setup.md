# Wazuh Server Installation

**Command**
```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash ./wazuh-install.sh -a
```
Once finished, the installer will output a URL similar to:

https://<WAZUH_IP>:5601/

Log in using the default credentials:

Username: admin
Password: admin

---

# Wazuh Agent Installation (Kali + Metasploitable2)

## Step 1 – Download the agent

```bash
curl -sO https://packages.wazuh.com/4.x/apt/wazuh-agent_4.7.0-1_amd64.deb
sudo dpkg -i wazuh-agent_4.7.0-1_amd64.deb
```
## Step 2 – Configure server IP
Edit the configuration file:

```bash
sudo nano /var/ossec/etc/ossec.conf
```

Change this section:
```bash
<server>
  <address>CHANGE_THIS_TO_WAZUH_IP</address>
</server>
```

## Step 3 – Start the agent
```bash
sudo systemctl enable --now wazuh-agent
```
✅ Repeat the same steps on the Metasploitable2 VM.
