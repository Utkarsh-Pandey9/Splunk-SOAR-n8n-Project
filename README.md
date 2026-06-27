# 🛡️ Automated Incident Response & Threat Detection Lab

An enterprise-grade simulation of a modern Security Operations Center (SOC) engineering project using an independent target endpoint, centralized SIEM logging, and an advanced automated playbook engine.

---

## 🏗️ Phase 1: Virtual Infrastructure & Base Environment Deployment

The foundation of this automated SOC lab consists of a hybrid virtual environment designed to host the attack platform, target endpoint, SIEM analytics engine, and the automation framework. To ensure system stability on a 16 GB host machine, memory allocations were strictly optimized to prevent resource contention.

### 💻 Infrastructure Architecture & Resource Matrix

| Component | Operating System | Deployment Model | Allocated RAM | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **Windows 11 Target** | Windows 11 Enterprise | VMware Workstation | 4.0 GB | Victim Endpoint / Telemetry Log Source |
| **Splunk Enterprise** | Ubuntu Server 24.04 LTS | Native Instance | 4.0 GB | Centralized SIEM / Log Ingestion Engine |
| **n8n Automation** | Ubuntu Server 24.04 LTS | Node.js / Docker | 1.5 GB | Advanced SOAR / Incident Orchestrator |
| **Attack Box** | Kali Linux | VMware Workstation | 2.0 GB | Adversary Emulation / Attack Generation |

---

### 🔍 Base Environment Verification & Proof of Deployment

To validate successful deployment and underlying network availability across the environment, the following baseline configurations have been verified and logged:

#### 1. Native Guest Console Configuration
* **Verification:** Successful initialization of the Ubuntu Server environment hosting the SIEM backbone. Network interface mapping confirmed via local shell execution.
![Ubuntu Local Interface Configuration](assets/01-splunk-local-console.png)

#### 2. Local Administration & Endpoint Baseline
* **Verification:** Deployment of the Windows 11 target environment. Bypassed default SaaS provisioning restrictions to implement a clean local administrator node for telemetry collection.
![Windows 11 Local Environment Baseline](assets/02-windows-local-console.png)

#### 3. Remote Host Management (SSH Connection)
* **Verification:** Active Secure Shell (SSH) connection established from the host system terminal directly into the Linux backend environment (`utkarsh@192.168.80.134`). This confirms full cross-platform access and network routing between the host machine and the virtual hypervisor tier.
![Host Terminal SSH Session](assets/03-ssh-remote-management.png)

---

## 🏗️ Phase 2: Splunk Enterprise Core Configuration & Log Ingestion Pipeline

Day 2 shifted focus toward establishing the centralized SIEM logging backbone, dynamically managing host storage infrastructure to bypass enterprise-grade security blocks, and mapping an active ingestion pipeline from the target endpoint.

### 🔍 Advanced Storage Management & CLI Configurations

During deployment, the Splunk indexing daemon halted search processes due to an automated safety threshold block requiring a minimum of 5GB of free space on the primary storage tier. To maintain infrastructure health on the local machine, a dynamic filesystem upgrade was executed live:

1. **Virtual Hardware Scaling:** Modified hypervisor settings to expand the provisioned storage allocation from **30 GB to 60 GB**.
2. **LVM Configuration:** Rescanned the physical block layer and extended the logical container natively:
   ```bash
   sudo pvresize /dev/sda
   sudo lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv

   ### ⚙️ Splunk Enterprise Base Configuration
Successfully configured the newly installed Splunk Enterprise instance on the Ubuntu Server (`my-splunk`) to automatically enable boot-start execution under the local `splunk` user account.

![Splunk Boot Start Configuration](assets/splunk_enable_boot_start_configuration.png)

---

## 🚀 Phase 3: n8n Automation Engine Deployment via Docker

Day 3 shifted focus toward deploying the orchestration and automation layer of the SOC infrastructure. The n8n automation engine was containerized to handle incident response playbooks and interact seamlessly with the existing SIEM telemetry.

### 💻 Containerization & System Preparation

To establish an isolated orchestration environment, the underlying container runtime was installed and workspace directories were structured:

1. **Docker Engine Installation:** Deployed the core Docker package (`docker.io`) to manage container lifecycles natively on the Ubuntu host.
2. **Workspace Initialization:** Created a dedicated operational directory to house configuration files and persistent data volumes:
   ```bash
   mkdir n8n-compose
   cd n8n-compose
