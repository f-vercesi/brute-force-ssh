# Incident Response — SSH Brute Force
 
## Incident Overview

- **Incident type:** SSH brute-force attack
- **Detection source:** Wazuh (log correlation)
- **Severity:** Medium
- **Confidence:** High
- **Status:** Attack stopped, no compromise detected
  
## Summary

Multiple failed SSH authentication attempts were detected against the host `soc-ssh-target`.
The activity originated from a single external source IP and targeted the `root` account.
No successful authentication or post-compromise activity was observed.

## Triage Actions

- Reviewed Wazuh alerts related to SSH authentication failures
- Verified repeated failed login attempts from the same source IP
- Confirmed absence of successful SSH logins

**In a real scenario, the scope must be checked to ensure no other hosts were targeted.**
 
## Scope Assessment

- **Affected host:** soc-ssh-target
- **Service impacted:** SSH
- **Targeted account:** root
- **Source IP:** 192.168.56.30
- **Lateral movement:** None observed
- **Privilege escalation:** Not observed

## Response Actions

- Documented attack indicators (source IP, target host, timestamps)
- Preserved relevant logs and alerts for investigation
- Classified incident according to SOC severity guidelines
- Prepared information for escalation
## Escalation

- **Escalated to:** SOC L2 / Security Engineering
- **Reason:** Repeated brute-force attempts against a privileged account
- **Evidence provided:** Wazuh alerts, authentication logs, timeline

## Recommended Mitigations

- Disable direct SSH login for the `root` account
- Enforce key-based SSH authentication
- Implement rate-limiting or brute-force protection (e.g., Fail2Ban)
- Continue monitoring SSH authentication events

## False Positive Considerations

The following benign scenarios were considered and ruled out:

- Authorized administrative activity
- Internal vulnerability scanning
- User password mistyping

The high frequency, repeated failures targeting a privileged account from a single non-trusted IP were inconsistent with normal behavior and aligned with brute-force automation.

## Final Assessment

- No system compromise detected
- Attack was unsuccessful
- Detection and response workflow validated
- Monitoring remains in place
