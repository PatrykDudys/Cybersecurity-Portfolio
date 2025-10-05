# Incident Report Analysis – DDoS Attack (ICMP Flood)

---

## Summary

| Aspect | Details |
|--------|---------|
| Summary | A malicious actor exploited an unconfigured firewall to send a flood of ICMP packets into the organisation's network which overwhelmed it and caused it to stop responding. The impacts of this were significant as it compromised the organisation's network for 2 hours, normal internal network traffic could not access any network resources, and there was disruption to client-facing services which could potentially lead to a loss in revenue. The malicious actor specifically targeted the internal network and critical servers necessary to run the different services. The incident management team immediately responded by blocking incoming ICMP packets, stopping all non-critical network services, and restoring critical network services. Following the immediate response, the team implemented a new firewall rule which limits the rate of incoming ICMP packets, added source IP verification on the firewall to check for spoofed IP addresses, introduced network monitoring software to detect irregular traffic, and added an IDS/IPS system to filter out specific ICMP traffic based on suspicious characteristics. |

---

## Identify

| Aspect | Details |
|--------|---------|
| Identify | The incident management team audited the systems, devices, and network and found that the malicious actor launched a DDoS attack by flooding the server with ICMP packets (ping flood). This attack exploited an unconfigured firewall, which allowed the malicious actor to flood it with ICMP packets undetected, overwhelming the server and causing it to stop responding. IP spoofing was further used to conceal the attack origin. |

---

## Protect

| Aspect | Details |
|--------|---------|
| Protect | To protect and prevent attacks like this in the future, several steps were taken. The firewall was configured to limit the rate of incoming ICMP packets and to perform source IP verification to detect and block spoofed traffic. Critical and non-critical network segments were identified and isolated, improving overall network security. Policies and procedures for firewall configuration and network access were reviewed and updated, and staff received further training to recognize and respond to DDoS attacks. Regular firewall audits were scheduled to ensure continued compliance with security standards. Additional protective measures included maintaining updated documentation of the network topology and critical assets, as well as reviewing patch management and system updates to minimize vulnerabilities. Through implementing these various protective controls, the organization strengthened its defenses against future volumetric attacks. |

---

## Detect

| Aspect | Details |
|--------|---------|
| Detect | To improve detection of potential security incidents, the organisation implemented network monitoring software capable of identifying abnormal traffic patterns in real time, such as Wireshark. An IDS/IPS system was configured to filter suspicious ICMP traffic and generate alerts for the security team. Baseline traffic patterns were established, making it easier to identify anomalies and react quickly. These detection measures increased the organisation’s ability to identify attacks early, minimize downtime, and maintain the integrity of critical services. |

---

## Respond

| Aspect | Details |
|--------|---------|
| Respond | The incident response team focused on containment, neutralization, and analysis. Measures included blocking all incoming ICMP traffic and temporarily isolating affected network segments. The security team applied updated firewall rules and IDS/IPS signatures to filter malicious traffic and prevent further disruption. The team also analyzed the attack by reviewing network logs, IDS alerts, and traffic patterns to understand the attack vector and identify vulnerabilities. Post-incident, a DDoS response playbook was developed to guide the team in future incidents, and penetration testing was conducted to further check for any vulnerabilities and help practice containing and defending against them. These steps ensured that the organisation could respond much quicker and effectively to similar attacks in the future. |

---

## Recover

| Aspect | Details |
|--------|---------|
| Recover | For recovery, the team focused on bringing the network back to functioning properly and ensuring all affected systems were fully operational. System integrity was verified to make sure no residual impact was caused by the attack. Firewall and IDS configurations were backed up, and normal traffic flow was monitored to confirm that protections were working as intended. |
