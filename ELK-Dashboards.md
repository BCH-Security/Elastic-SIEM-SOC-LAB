#  Elastic SIEM Dashboards


##  Creating a Dashboard for Failed Login Attempts
---
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



