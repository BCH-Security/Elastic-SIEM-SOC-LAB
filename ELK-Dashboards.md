#  Elastic SIEM Dashboards


##  Creating a Dashboard for Failed Login Attempts

### 1. Create Visualization

* Visting the dashboard page
![dashboard](Images/dashboard-1.png)

* Creating new dashboard
![dashboard](Images/dashboard-2.png)

* Creating visualization
![dashboard](Images/dashboard-3.png)


### 2. Add Filter

* Adding Filter (In our case event code 4625)
![dashboard](Images/dashboard-4.png)
![dashboard](Images/dashboard-5.png)



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
