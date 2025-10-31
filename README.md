# 🔧 Equipment Reliability Analysis (Advanced SQL Project)

## Project Overview
This project demonstrates advanced data engineering and analysis using **SQL** to solve a real-world industrial problem. I designed and built a relational database (in SQLite) to simulate an equipment maintenance and sensor-logging system.

The goal was to move beyond simple data retrieval (`SELECT *`) and write complex, analytical queries to answer critical business questions about machine reliability.

***

## 🛠️ Technology Stack & Key SQL Concepts

* **Database:** SQLite (run locally in VS Code)
* **Database Design:** Relational Schema (3 tables with Primary/Foreign Keys)
* **Advanced SQL Techniques:**
    * **Window Functions:** `LAG()`, `AVG() OVER()`
    * **Partitions:** `PARTITION BY`
    * **Time-Series Analysis:** `ROWS BETWEEN PRECEDING AND CURRENT ROW`
    * **Joins:** `JOIN ... ON`
    * **CTEs (Common Table Expressions):** `WITH` clauses
    * **Date Functions:** `JULIANDAY()`

***

## 🚀 Key Business Questions & Analysis

This project answers three critical engineering questions by querying the database.

### 1. Analysis: Mean Time Between Failures (MTBF)
* **Question:** How long does each machine run before it fails again?
* **SQL Skill:** Used the `LAG()` window function, partitioned by `Machine_ID`, to calculate the number of days between each failure and the previous one. This is a core metric for any reliability engineer.

### 2. Analysis: Sensor Time-Series (Rolling Average)
* **Question:** How can we smooth out noisy sensor data to spot real trends?
* **SQL Skill:** Used `AVG() OVER()` with a `ROWS BETWEEN 6 PRECEDING AND CURRENT ROW` clause. This calculates a 7-day rolling average temperature for each machine, making it easy to see gradual overheating.

### 3. Analysis: Pre-Failure Sensor Anomalies
* **Question:** What do the sensors look like in the 3 days *just before* a machine breaks?
* **SQL Skill:** Used a **CTE** and a `JOIN` to link the `SENSOR_LOG` table to the `MAINTENANCE_LOG` table. The query finds the average temperature and vibration in the 72-hour window *before* each recorded failure, helping to identify failure signatures.
