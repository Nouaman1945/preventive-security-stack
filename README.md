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

## 🧠 Why Sysmon is Essential

**Sysmon (System Monitor)** is a crucial component in this stack. It is responsible for collecting detailed event logs from the Windows endpoint — including process creation, network connections, registry changes, and file modifications — which are then analyzed by Wazuh.

Without Sysmon, you won’t capture rich behavioral data necessary for meaningful threat detection and enrichment.

---

## 🏁 Installing Sysmon on Windows

1. Download Sysmon from the official [Sysinternals site](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)
2. Download a configuration file (you can use [SwiftOnSecurity's sysmon-config](https://github.com/SwiftOnSecurity/sysmon-config) or write your own)
3. Open CMD as Administrator and run:

```cmd
sysmon64.exe -accepteula -i sysmonconfig.xml


Access components:

Wazuh Dashboard → https://localhost:5601
admin:SecretPassword

MISP Web UI → https://localhost:8443
admin@admin.test:admin

Logstash is headless and runs in the background
