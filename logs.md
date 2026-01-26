# Log Sources

This section lists the log sources used during analysis.

---
## Target (Agent)

 `/var/log/auth.log`

- Native Linux authentication log.
- Source of SSH login attempts (successful and failed).
- Primary evidence of brute-force activity at the operating system level.

 `/var/ossec/logs/ossec.log`

- Wazuh agent internal log.
- Shows how the agent parses, tags, and forwards SSH-related events to the manager.

 `/var/ossec/logs/archives/archives.json`

- Local archive of events processed by the agent.
- Used to validate that SSH events were correctly captured before transmission.
## Wazuh Manager

 `/var/ossec/logs/archives/archives.json`

- Centralized raw log storage for events received from all agents.
- Used to confirm high-frequency SSH authentication failures from the attacker IP.

 `/var/ossec/logs/ossec.log`

- Wazuh manager internal processing log.
- Confirms rule execution, alert generation, and event handling.
 
 `/var/ossec/logs/alerts/alerts.json`

- Wazuh-generated security alerts after rule evaluation and correlation.
- Source of the SSH brute-force detection alert.

---
## Notes:

SSH authentication events originate on the **target system** and are forwarded by the **Wazuh agent**.

Alert generation and correlation occur **only on the Wazuh Manager**, but
**evidence was validated at both the agent and manager levels to confirm end-to-end visibility.**
