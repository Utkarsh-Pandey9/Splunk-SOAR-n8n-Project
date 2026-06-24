# 🛡️ Automated Incident Response & Threat Detection Lab

An enterprise-grade simulation of a modern Security Operations Center (SOC) engineering project using an independent target endpoint, centralized SIEM logging, and an advanced automated playbook engine.

---

## 🏗️ Phase 1: Virtual Infrastructure & Base Environment Deployment

The foundation of this automated SOC lab consists of a hybrid virtual environment designed to host the target endpoint, the SIEM analytics engine, and the automation framework. To ensure system stability on a 16 GB host machine, memory allocations were strictly optimized to prevent resource contention.

### 💻 Infrastructure Architecture & Resource Matrix

| Component | Operating System | Deployment Model | Allocated RAM | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **Windows 11 Target** | Windows 11 Enterprise | VMware Workstation | 4.0 GB | Victim Endpoint / Telemetry Log Source |
| **Splunk Enterprise** | Ubuntu Server 24.04 LTS | Native Instance | 4.0 GB | Centralized SIEM / Log Ingestion Engine |
| **n8n Automation** | Ubuntu Server 24.04 LTS | Node.js / Docker | 1.5 GB | Advanced SOAR / Incident Orchestrator |

---

### 🔍 Base Environment Verification & Proof of Deployment

To validate successful deployment and underlying network availability across the environment, the following baseline configurations have been verified and logged:

#### 1. Native Guest Console Configuration
* **Verification:** Successful initialization of the Ubuntu Server environment hosting the SIEM backbone. Network interface mapping confirmed via local shell execution.
![Ubuntu Local Interface Configuration](assets/Screenshot%202026-06-24%20195523.png)

#### 2. Local Administration & Endpoint Baseline
* **Verification:** Deployment of the Windows 11 target environment. Bypassed default SaaS provisioning restrictions to implement a clean local administrator node for telemetry collection.
![Windows 11 Local Environment Baseline](assets/Screenshot%202026-06-24%20195556.png)

#### 3. Remote Host Management (SSH Connection)
* **Verification:** Active Secure Shell (SSH) connection established from the host system terminal directly into the Linux backend environment (`utkarsh@192.168.80.134`). This confirms full cross-platform access and network routing between the host machine and the virtual hypervisor tier.
![Host Terminal SSH Session](assets/Screenshot%202026-06-24%20200918.png)
