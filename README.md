# Wazuh-SIEM-GCP-Lab
![Screenshot (49)](https://github.com/user-attachments/assets/79b0233b-31ac-4ba5-85a3-9212eac05a36)


## Project Overview
This repository documents the setup and configuration of a hands-on Security Information and Event Management (SIEM) laboratory using Wazuh on Google Cloud Platform (GCP). The goal of this project is to gain practical experience in deploying a SIEM, collecting logs from diverse endpoints, analyzing security events, and understanding core security operations principles.

## Architecture
The lab environment consists of:
- **Wazuh Manager:** Deployed on an Ubuntu VM on GCP, acting as the central SIEM server.
- **Wazuh Agents:** Three active agents sending logs to the manager:
    - **GCP Ubuntu Agent 1:** A general-purpose Linux endpoint for monitoring system logs.
    - **GCP Ubuntu Web Server Agent:** An Ubuntu VM hosting an Apache web server, configured for web application log monitoring and attack simulation.
    - **Local Windows Workstation Agent:** My primary Windows machine, collecting critical Windows Event Logs.
- **GCP Custom VPC:** A dedicated network for lab resources, isolated for security.
- **GCP Firewall Rules:** Configured to control traffic flow securely between components and allow external access to the Wazuh Dashboard.

## Technologies Used
- **SIEM:** Wazuh (Manager, Indexer, Dashboard, Agents)
- **Cloud Platform:** Google Cloud Platform (Compute Engine, VPC Network, Firewall, Pub/Sub - *future*)
- **Operating Systems:** Ubuntu Server 22.04 LTS, Windows 10/11
- **Containerization:** Docker, Docker Compose
- **Web Server:** Apache2 (on Web Server Agent)
- **Tools:** `gcloud` CLI, SSH, `curl`, `nano`

## Key Achievements

![Screenshot (50)](https://github.com/user-attachments/assets/1f2f55cc-a755-491d-b51b-8488836c2f1f)

- Successfully provisioned and configured GCP Compute Engine VMs and a custom VPC network.
- Implemented granular GCP firewall rules for secure network segmentation.
- Deployed Wazuh Manager using Docker Compose on an Ubuntu VM.
- Installed and configured Wazuh Agents on multiple Ubuntu VMs and a local Windows workstation.
- Established real-time log ingestion and security event monitoring for diverse endpoints.
- Gained hands-on experience with:
    - Cloud VM instance management
    - Network configuration and security best practices (firewalls, tags)
    - Docker container deployment and management
    - Wazuh agent installation and configuration
    - Basic log analysis and dashboard navigation
    - Setting up a web server for security monitoring scenarios

## Setup Guide (High-Level Steps)
*(Here, you'd add the condensed steps you followed. Be careful not to include any sensitive IPs or credentials)*

1.  **GCP VPC & Subnet Creation:**
    * `default-vpc`
2.  **GCP Firewall Rules:**
    * `allow-ssh-wazuh-lab` (TCP:22 for `wazuh-vm` tag)
    * `wazuh-ports` (TCP:1514, 1515, 5601 for `wazuh-manager-vm` tag)
    * `allow-icmp-wazuh-lab` (ICMP for `wazuh-vm` tag)
    * `allow-web-server-http-https` (TCP:80, 443 for `web-server-vm` tag)
3.  **Wazuh Manager VM Deployment:**
    * `e2-medium` Ubuntu 22.04 VM with `wazuh-vm` and `wazuh-manager-vm` tags.
    * Docker & Docker Compose installation.
    * Wazuh Docker stack deployment (`wazuh-docker/single-node`).
4.  **Wazuh Agent VM Deployments (Ubuntu 1 & Web Server):**
    * `e2-micro` Ubuntu 22.04 VMs with `wazuh-vm` tag (and `web-server-vm` for the web server).
    * Wazuh Agent installation.
    * `ossec.conf` configuration to point to Wazuh Manager External IP.
    * Apache2 installation on Web Server VM.
    * `ossec.conf` modification to monitor Apache logs.
5.  **Local Windows Agent Deployment:**
    * Wazuh Agent MSI installation on Windows machine.
    * `ossec.conf` modification for specific Windows Event Channel logs.

## Next Steps / Future Enhancements
-   Integrate GCP Cloud Audit Logs and VPC Flow Logs into Wazuh via Pub/Sub.
-   Develop custom Wazuh rules and decoders for specific threat detection scenarios.
-   Configure Active Response for automated threat mitigation.
-   Perform basic attack simulations (e.g., port scanning, brute-force attempts) to test detection capabilities.
-   Explore Wazuh's vulnerability detection and compliance modules.
-   Implement dashboards and visualizations for specific use cases.

---
