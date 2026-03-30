#  Elastic SIEM SOC Lab

##  Overview

This project demonstrates a hands-on **Security Operations Center (SOC) lab** built using the Elastic Stack for monitoring, detection, and threat hunting.

---

##  What is SIEM?

**SIEM (Security Information and Event Management)** is a solution that collects, analyzes, and correlates logs from multiple sources in real time to detect suspicious activity and security threats.

Key capabilities:

* Log aggregation
* Real-time monitoring
* Threat detection
* Incident response

---

##  What is Elastic?

**Elastic (Elastic Stack / ELK Stack)** is a powerful open-source platform used for search, analytics, and visualization.

It includes:

* **Elasticsearch** → Data storage and search engine
* **Logstash / Beats** → Data collection and ingestion
* **Kibana** → Data visualization and dashboards

---

##  Lab Environment

This SOC lab consists of three main machines:

###  Ubuntu Server (SIEM Server)

* Hosts:

  * Elasticsearch
  * Kibana
* Responsible for storing and analyzing logs

---

###  Windows 11 Workstation (Victim Machine)

* Configured with:

  * **Winlogbeat** (running as a service)
* Sends Windows event logs to Elasticsearch

---

###  Attacker Machine (Kali Linux)

* Used to simulate attacks
* Generates logs (e.g., failed login attempts)

---

##  Setup: Installing Elastic Stack with Docker

### 1. Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker
```

---

### 2. Create the Elastic Stack using Docker

```bash
docker compose up -d
```


---


##  Beat Setup: Installing winlogbeat Service

### 1. Download Winlogbeat
Winlogbeat can be downloaded from [winlogbeat-9.3.2-windows-x86_64.zip](https://artifacts.elastic.co/downloads/beats/winlogbeat/winlogbeat-9.3.2-windows-x86_64.zip)



### 2. Install winlogbeat Service
* Extract winlogbeat-9.3.2-windows-x86_64.zip
* Open cmd as administrator and run the powershell script:
```bash
c:\Users\REDACTED\Downloads\winlogbeat-9.3.2-windows-x86_64> dir
 Le volume dans le lecteur C n’a pas de nom.
 Le numéro de série du volume est CC1A-F90E

 Répertoire de c:\Users\REDACTED\Downloads\winlogbeat-9.3.2-windows-x86_64> dir

29/03/2026  18:57    <DIR>          .
29/03/2026  17:58    <DIR>          ..
29/03/2026  17:58                41 .build_hash.txt
29/03/2026  19:05    <DIR>          data
29/03/2026  17:58           413 715 fields.yml
29/03/2026  17:58             3 224 install-service-winlogbeat.ps1
29/03/2026  17:58    <DIR>          kibana
29/03/2026  17:58            13 675 LICENSE.txt
29/03/2026  18:57    <DIR>          logs
29/03/2026  17:58    <DIR>          module
29/03/2026  17:58         4 757 457 NOTICE.txt
29/03/2026  17:58               832 README.md
29/03/2026  17:58               298 uninstall-service-winlogbeat.ps1
29/03/2026  17:58       117 241 824 winlogbeat.exe
29/03/2026  17:58            67 657 winlogbeat.reference.yml
29/03/2026  18:58             7 758 winlogbeat.yml
              10 fichier(s)      122 506 481 octets
               6 Rép(s)  42 238 472 192 octets libres
```            


```
http://localhost:5601
```

---

## 🔍 Threat Hunting Example

### 🎯 Detect Failed Logon Attempts (Event ID 4625)

Windows Event ID **4625** indicates a **failed login attempt**.

### 🔎 Search in Kibana (KQL)

```kql
event.code: "4625"
```

---

### 📊 Useful Fields

* `winlog.event_data.TargetUserName`
* `source.ip`
* `host.name`

---

### 🚨 Use Case

Detect:

* Brute force attacks
* Unauthorized access attempts
* Suspicious login behavior

---

## 📈 Creating a Dashboard for Failed Login Attempts

### 1. Create Visualization

* Go to **Kibana → Visualize**
* Choose:

  * Bar chart or Data table

---

### 2. Configure

* Index pattern: `winlogbeat-*`
* Metric: Count
* Breakdown by:

  * `source.ip` or `TargetUserName`

---

### 3. Add Filter

```kql
event.code: "4625"
```

---

### 4. Save Visualization

---

### 5. Create Dashboard

* Go to **Dashboard → Create new dashboard**
* Add your visualization
* Save as: **Failed Login Monitoring**

---

## 🛡️ Outcome

This lab allows you to:

* Simulate real-world attacks
* Collect and analyze logs
* Detect suspicious activity
* Build SOC-level dashboards

---

## 📎 Future Improvements

* Add alerts using Elastic Detection Rules
* Integrate Filebeat for Linux logs
* Simulate more attack scenarios (RDP brute force, privilege escalation)

---

## 👨‍💻 Author

BCH-Security
