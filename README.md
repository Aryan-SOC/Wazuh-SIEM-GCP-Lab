# SIEM Lab Project: Wazuh + Splunk + Suricata + Jira Service Management on GCP & VirtualBox

A hands-on, production-inspired SIEM and **Incident Response (IR)** lab built to simulate real-world security operations using open-source tools, Jira Service Management, and cloud infrastructure.

---

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[LinkedIn](www.linkedin.com/in/shewag-bhattarai-103424236)

---

## 📌 Project Overview

This project demonstrates the configuration and integration of a hybrid SIEM + **Incident Response** environment using:

- **Wazuh** for log aggregation, threat detection, and endpoint security monitoring
- **Splunk Enterprise** for data analysis, alerting, and visualization
- **Suricata** for network intrusion detection (currently inactive for data forwarding – see below)
- **Jira Service Management (Cloud Free Tier)** for centralized incident (case) management and tracking

Deployed across Google Cloud Platform (GCP) and local VirtualBox VMs, this lab simulates real attack/defense scenarios using Windows, Linux, and Kali systems, with a strong focus on **Incident Response (IR)** workflows, ticketing, and post-incident analysis.

### **Highlight:**
- Integration of Wazuh into Splunk enables centralized alert visualization and correlation across all endpoint types — Linux, Windows, and IDS logs.
- **Jira Service Management** is integrated as the core platform for incident case management: all Splunk-triggered security alerts are manually ticketed in Jira, mirroring real-world SOC IR workflows (see below for details).
- **Detailed incident reports, analysis, and post-mortem documentation for simulated attacks are maintained in a dedicated repository: [Home-SOC-Incident-Reports](https://github.com/Aryan-SOC/Home-SOC-Incident-Reports).**

---

## ⚙️ Lab Infrastructure

| Component              | Description                                                                                              |
|------------------------|----------------------------------------------------------------------------------------------------------|
| **Wazuh Manager**      | Central log collection, threat detection, and agent management                                           |
| **Wazuh Agents**       | Installed on Windows, Linux, Kali, forwarding system and security logs                                   |
| **Splunk Enterprise**  | SIEM dashboard, search, alerting, and integration point for all security data                           |
| **Suricata IDS**       | **(Currently inactive/discontinued for data forwarding in this phase. Retained for future expansion or reference.)** |
| **Jira Service Management** | Cloud-based case and incident management system (manual ticket creation from Splunk alerts, see below) |
| **GCP VMs (Ubuntu)**   | Host Wazuh Manager, Splunk, Suricata, and sample endpoints                                              |
| **VirtualBox VMs**     | Simulate on-prem endpoints (Windows, Linux, Kali)                                                       |

---

## 🧩 Component Configuration

- **Wazuh Agents:** Deployed on all endpoint VMs (Windows, Linux, Kali) for log forwarding and security monitoring.
- **Splunk:** Receives and correlates all Wazuh alerts; custom dashboards and alerts configured for IR.
- **Suricata:** *Inactive for current data flow; focus is on endpoint security and SIEM correlation. Network IDS capability available for future phases.*
- **Jira Service Management:** Configured as the centralized case management platform for all incidents.

---

## 🚨 Incident Response (IR) & Jira Service Management Integration

- **Centralized IR Case Management:**  
  Jira Service Management (Cloud Free Tier) is integrated as the platform for tracking and managing all security incidents and cases arising from Splunk alerts.
- **Manual Ticket Creation:**  
  Due to free-tier limitations (no automated webhooks or outbound integrations), Splunk alert notifications require **manual creation of Jira tickets**. Each alert triggers a human-driven workflow:
  - Review alert in Splunk
  - Open Jira Service Management
  - Categorize the incident, document details, set priority/status, and assign owner
  - Track response actions and resolution within Jira

- **Learning Benefits:**  
  This manual approach provides hands-on experience with:
  - Incident categorization and prioritization  
  - Writing detailed case documentation  
  - Status tracking and workflow management  
  - Simulating authentic SOC IR case handling and post-mortem analysis

- **Continuous Improvement:**  
  Future plans include exploring open-source SOAR/case management solutions or custom webhooks for automating ticket creation and response workflows as part of ongoing lab enhancements.

---

## 🧪 Attack Simulation & Validation

- Simulated attacks (e.g., malware, privilege escalation, suspicious process execution) are performed across endpoints and monitored through the SIEM pipeline.
- **Note:**  
  *For detailed incident reports, IR analysis, and post-mortem documentation for these simulated attacks, visit the dedicated repo: [Home-SOC-Incident-Reports](https://github.com/Aryan-SOC/Home-SOC-Incident-Reports).*

---

## ✅ Key Outcomes

**Incident Response (IR) Focused:**
- End-to-end IR workflow simulation: detection, triage, investigation, case management, and documentation

**Log Forwarding Pipeline:**
- Endpoint/IDS logs → Wazuh Agent → Wazuh Manager → Splunk Universal Forwarder → Splunk Index

**Enterprise SOC Simulation:**
- Modular, production-inspired detection stack
- Real operational challenges solved (e.g., log volume, agent communication, network segmentation)

**Cross-platform Coverage:**
- Linux, Windows, (Suricata data when active), both cloud and on-prem environments

**Centralized Alert Visibility:**
- All Wazuh alerts from endpoints visible and actionable in Splunk, with downstream IR case escalation in Jira

---

## 📎 Assumptions

- Ubuntu/Docker/Splunk/Wazuh are pre-installed
- GCP & VirtualBox networking, SSH access are configured
- Basic installation steps are not included in this documentation

---

## 📚 Resources

- [Wazuh Documentation](https://documentation.wazuh.com/)
- [Splunk Docs](https://docs.splunk.com/)
- [Suricata Docs](https://suricata.readthedocs.io/) *(reference; currently inactive in this phase)*
- [Jira Service Management](https://www.atlassian.com/software/jira/service-management)
- [Home-SOC-Incident-Reports](https://github.com/Aryan-SOC/Home-SOC-Incident-Reports) – **repository for detailed incident reports, IR analysis, and post-mortems**

---

## 🙌 Contribute or Connect

Have suggestions, feedback, or want to collaborate on lab setups like this? Let’s connect and grow together in cybersecurity!

**Author:** Shewag Bhattarai  
**LinkedIn:** [www.linkedin.com/in/shewag-bhattarai-103424236](www.linkedin.com/in/shewag-bhattarai-103424236)  
**License:** MIT

---
