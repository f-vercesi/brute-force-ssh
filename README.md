# SSH Brute-Force Detection & Response (SOC L1 Lab)

This repository documents a hands-on SOC Level 1 lab focused on detecting and responding to an SSH brute-force attack using **Wazuh SIEM**.

The objective is to demonstrate:

- Understanding of SSH brute-force behavior
- Log analysis from Linux and Wazuh
- Alert triage and validation
- Basic incident response actions aligned with a SOC L1 role

---
 
## Environment Overview
 
### Attacker

- OS: Kali Linux
- IP: `192.168.56.30`
- Role: External attacker performing SSH brute-force
### Target

- OS: Ubuntu Server 22.04
- Hostname: `soc-target-ssh`
- User: `socuser`
- IP: `192.168.56.20`
- Wazuh Agent installed
### SIEM / Manager

- OS: Ubuntu Server 22.04
- Hostname: `soc-server`
- User: `socadmin`
- IP: `192.168.56.10`
- Wazuh Manager
  
---
  
## Attack Summary
  
A brute-force attack was launched from the Kali attacker against the SSH service on the Ubuntu target.

The Wazuh agent collected authentication logs and forwarded them to the Wazuh Manager, where alerts were generated and analyzed.
