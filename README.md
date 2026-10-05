#  Optimizing Public Transportation: Predicting Monthly Transit Ridership

## Project Overview
Public transportation agencies face significant challenges in estimating future passenger demand[cite: 2.5]. Accurate forecasting is essential for operational planning, including scheduling vehicles, allocating staff, and optimizing budgets[cite: 2.2, 2.5]. 

This project delivers an end-to-end data analytics and predictive modeling framework using **R** and an interactive **Power BI** dashboard[cite: 2.2]. By analyzing historical transit data from the U.S. National Transit Database (NTD), we predict monthly transit ridership (Unlinked Passenger Trips - UPT) to enable proactive resource planning[cite: 2.2].

---

---

##  Dataset & Scope
* **Source:** U.S. National Transit Database (NTD)[cite: 2.2]
* **Primary Analysis Scope:** 2014 – Present (focusing on recent travel patterns and post-COVID-19 recovery patterns)[cite: 2.2].
* **Key Variables:**
  * `UPT` (Unlinked Passenger Trips): Main Target Variable[cite: 2.2].
  * `VRH` (Vehicle Revenue Hours) & `VRM` (Vehicle Revenue Miles): Operational Supply Metrics[cite: 2.2].
  * `VOMS` (Vehicles Operated in Maximum Service)[cite: 2.2].
  * Meta Attributes: Agency, State, Transportation Mode, Type of Service (TOS)[cite: 2.2].

---

##  Tech Stack & Workflow
1. **Data Cleaning & Engineering (R / Google Colab):**
   * Standardized column schema and filtered non-positive/duplicate records[cite: 2.2].
   * Created time-based lag features (`Lag 1`, `Lag 3`, `Lag 6`, `Lag 12`) and rolling averages (`3-month` and `12-month`)[cite: 2.2].
2. **Predictive Modeling (R):**
   * Evaluated multiple approaches: **Linear Regression**, **ARIMA**, and **Random Forest**[cite: 2.2].
   * **Selected Model:** **Random Forest** achieved the best performance with a **MAPE of 3.35%**[cite: 2.2].
3. **Executive Dashboard (Power BI):**
   * Interactive dashboard for decision-makers featuring KPI cards, mode breakdowns, and future monthly demand forecasts[cite: 2.2].

---

##  Key Findings
* **Post-COVID Recovery:** Ridership is continuing to recover but growth is slowing down (~79% of 2019 levels as of 2024)[cite: 2.2].
* **Seasonality:** Monthly demand exhibits a stable, repeating seasonal pattern both before and after COVID-19[cite: 2.2].
* **Demand Concentration:** Demand is heavily concentrated in Bus and Rail modes, led by major state agencies (e.g., MTA in New York)[cite: 2.2].

---

##  Project Links & Resources
* 📓 **Google Colab Notebook:** https://colab.research.google.com/drive/162V8PdrdAaf3BUE6rGL7uoqSKJzMJARS?usp=drive_link
* 📊 **Power BI Dashboard:** https://app.powerbi.com/links/IpRLsnG_YE?ctid=55488759-d4c9-4a95-ae92-ada1488c4053&pbi_source=linkShare&bookmarkGuid=1667227a-493d-4d28-a54d-97767de5ba6f
* 📂 **Raw Dataset:** https://drive.google.com/file/d/1cSnK7KUUCt5t2yNQDJfpMA59XBrVFNhi/view?usp=sharing
* 📂 **Cleaned Dataset:** https://drive.google.com/file/d/16BT9v7Nh6OSDPiCQWJA-n2svXF-UeQlY/view?usp=sharing
