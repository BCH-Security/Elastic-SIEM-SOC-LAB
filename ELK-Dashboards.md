#  Elastic SIEM Dashboards (Failed Login Monitoring)

##  Introduction

This document focuses on building and analyzing **failed login monitoring dashboards** using the Elastic SIEM stack. It demonstrates how to simulate real-world attack scenarios and visualize security events for effective threat detection.

In this lab, we generate failed authentication attempts through controlled brute-force activity and capture these events using Winlogbeat. The logs are then ingested into Elasticsearch and visualized in Kibana to provide actionable insights.

The goal is to help security analysts:

* Detect brute-force attacks in real time
* Identify suspicious login patterns
* Monitor attacker behavior through log analysis
* Build meaningful dashboards for SOC operations

This hands-on approach bridges the gap between attack simulation and defensive monitoring, making it ideal for learning practical SIEM and threat hunting skills.

---

##  Attack Simulation

* Use Hydra to Bruteforce RDP Login Credentials

```bash
hydra -L /usr/share/wordlists/SecLists-master/Usernames/top-usernames-shortlist.txt -P /usr/share/wordlists/SecLists-master/Passwords/Leaked-Databases/rockyou-05.txt rdp://Target-IP:3389 -t 16 -I -V
```

---

##  Creating a Dashboard for Failed Login Attempts

### 1. Create Visualization

* Visting the dashboard page
![dashboard](Images/dashboard-1.png)

* Creating new dashboard
![dashboard](Images/dashboard-2.png)

* Creating visualization
![dashboard](Images/dashboard-3.png)

---
### 2. Add Filter

* Adding Filter (In our case event code 4625)
![dashboard](Images/dashboard-4.png)
![dashboard](Images/dashboard-5.png)

---
### 3. Configuring visualization type and Data view
* Choosing Table for Visualization Type
![dashboard](Images/dashboard-6.png)

* Selecting winlogbeat data view
![dashboard](Images/dashboard-7.png)

---
### 4. Add Fields
* Click on `Add or drag-and-drop a field`
![dashboard](Images/dashboard-8.png)

* Adding the field `winlog.event_data.TargetUserName`
![dashboard](Images/dashboard-9.png)

* Adding metrics (count: Number of Login attempts)
![dashboard](Images/dashboard-10.png)
![dashboard](Images/dashboard-11.png)
![dashboard](Images/dashboard-12.png)

* Adding the field `host.hostname`
![dashboard](Images/dashboard-13.png)

* Adding the field `winlog.event_data.LogonType`
![dashboard](Images/dashboard-14.png)



---
### 4. Save Visualization
* Click on `Save and return` 
![dashboard](Images/dashboard-15.png)

* Click on `Save`
![dashboard](Images/dashboard-16.png)

* Give name for the dashboard and click on  `Save`
![dashboard](Images/dashboard-17.png)


## Refining The Visualization
Suppose the SOC Manager suggested adding the source IP Address to the dashboard

* Click on `Edit Visualization`
![dashboard](Images/dashboard-18.png)


* Adding the field `winlog.event_data.IpAddress`
![dashboard](Images/dashboard-19.png)

* Apply the new changes and save
![dashboard](Images/dashboard-20.png)
![dashboard](Images/dashboard-21.png)




---

##  Outcome

This lab allows you to:
* Simulate real-world attacks
* Build SOC-level dashboards
* Detect Failed Login Attempts
* Detect suspicious activity
