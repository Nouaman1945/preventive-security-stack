# Preventive Security Stack

An integrated security solution combining **Wazuh**, **MISP** (Malware Information Sharing Platform), and **Logstash**, designed to deliver **real-time threat detection**, **log enrichment**, and **proactive analysis**. This stack forms the basis of a preventive security analysis module, suitable for academic research, SOCs, or cybersecurity lab environments.

---

## 🔍 Project Overview

This stack aims to:
- Collect and monitor system logs using **Wazuh**
- Correlate logs and alerts through **Logstash**
- Enrich alerts with threat intelligence from **MISP**
- Provide visibility for potential threats through dashboards

The architecture is containerized using **Docker** to simplify deployment and ensure modularity.

---

## 📦 Stack Components

| Component | Role |
|----------|------|
| **Wazuh Manager** | Collects and analyzes endpoint logs |
| **Wazuh Agent** (Windows) | Installed on the endpoint (Sysmon used for event logging) |
| **Wazuh Dashboard** | Visualizes alerts |
| **Logstash** | Filters and transforms Wazuh alerts, enriches them with MISP IoCs |
| **MISP** | Stores and serves threat intelligence (IoCs, events, attributes) |
| **Docker** | Containerizes and orchestrates the full environment |

---

## 🛠️ Deployment (Docker)

> ⚠️ Prerequisite: Docker & Docker Compose installed.

Clone the repository:

```bash
git clone https://github.com/Nouaman1945/preventive-security-stack.git
cd preventive-security-stack
