# 🏥 From Raw Data to Strategic Insights: Building a Healthcare Analytics Powerhouse

A full-scale, end-to-end **healthcare analytics platform** built using Snowflake, dbt, Mage, and Power BI. This project transforms siloed data from multiple hospitals into a **unified, secure, and scalable** analytics solution — empowering business owners with actionable insights to optimize operations and drive strategic decisions.

---

## 📈 Business Challenge

**Scenario**: A business owner has two successful hospitals and recently acquired a third. The problem?

- 🚫 No consolidated view across all hospitals
- 🔍 Difficulty tracking key KPIs like doctor performance or patient costs
- 📉 Manual, error-prone analytics delayed business decisions

> **Goal**: Build a single, centralized platform to unify all data and provide near real-time, actionable insights across all hospitals.

---

## 🏗️ Solution Overview

Our data engineering team of 4 built a robust Medallion Architecture-based pipeline powered by:

- 🧊 **Snowflake** (data lakehouse with Bronze, Silver, Gold layers)
- 🛠 **dbt** for transformations and modeling
- 🧪 **Mage** for ingestion and orchestration
- 📊 **Power BI** for dashboards
- 🔐 **RBAC, Data Masking, and Lineage** for data governance

---

## 🧱 Architecture: Medallion Design

### 🔹 Bronze Layer – Raw Ingestion
- Tool: Mage + Python connectors
- Source: Microsoft SQL Server (per hospital)
- Action: Land raw, unprocessed data in Snowflake (one-to-one mapping from source)

### 🔸 Silver Layer – Cleaned & Unified
- Tool: dbt + Snowflake
- Action: 
  - Clean nulls, standardize formats, remove duplicates
  - Merge 15 tables from each hospital into 15 unified cleaned tables (e.g., patients, doctors)

### 🥇 Gold Layer – Star Schema for Analytics
- Tool: dbt
- Structure:
  - `dim_patients`, `dim_doctors`, `dim_departments`, `dim_date`, `dim_medical_stock`
  - `fact_appointments`, `fact_satisfaction`, `fact_bills`, etc.
- Purpose: Designed for fast, reliable BI querying

---

## 📊 Visualization: Power BI Dashboards

Using **Direct Query** from Power BI to Snowflake’s Gold Layer, we created 5 executive dashboards:

1. **👨‍⚕️ Patient Dashboard**  
   Tracks admissions, services, costs, diagnoses, attending doctors.

2. **🩺 Doctor Dashboard**  
   Ratings, schedule, and commissions.

3. **💰 Finance Dashboard**  
   Revenue per department and hospital.

4. **🏥 Hospital Overview**  
   Beds, departments, services – across all 3 hospitals.

5. **📋 Executive Summary**  
   High-level overview across KPIs for fast strategic decisions.

> 🔒 *Note: All data is anonymized or simulated for privacy.*

---

## 🔄 Orchestration, CI/CD, & QA

- **Mage**: Schedules and runs ingestion + transformation jobs
- **CI/CD**: Git + Docker used for version control and automation
- **Testing**:
  - `not_null`, `unique`, row count tests using dbt
  - Ensures data quality at each stage

---

## 🔐 Data Governance & Security

| Feature              | Tool Used            |
|----------------------|----------------------|
| Access Control        | Snowflake RBAC       |
| Sensitive Data Masking | Snowflake Dynamic Masking |
| Data Lineage          | dbt (auto lineage)   |

- Ensured **HIPAA-compliant** handling of PII
- Protected patient & doctor identities

---

## 🚀 Agile Development

We followed Agile best practices:

- 🏃 Daily standups
- 📋 Azure Boards to manage epics, features, and tasks
- 🧠 Iterative delivery with continuous feedback

Team Roles:

- 🛠 ETL Engineers
- 📐 Data Architects
- 👩‍💻 QA Engineers
- 📊 Reporting Analysts

> Everyone contributed cross-functionally while owning key deliverables.

---

## ⚒️ Tech Stack

| Area                   | Tool/Tech                |
|------------------------|--------------------------|
| Source Data            | SQL Server               |
| Ingestion & Orchestration | Mage (Python)           |
| Transformation         | dbt (SQL + Jinja)        |
| Warehouse              | Snowflake                |
| BI Visualization       | Power BI (Direct Query)  |
| DevOps / CI-CD         | Git, Docker              |
| Project Management     | Azure Boards             |

---

## ⚠️ Key Challenges & Solutions

### 1. **Data Unification Across Hospitals**
- **Challenge**: Merging 3 sets of schemas
- **Solution**: Surrogate keys + unified models in Silver layer

### 2. **Relationship Issues in Power BI**
- **Challenge**: Broken visualizations due to wrong joins
- **Solution**: Star schema design + relationship tuning in BI

### 3. **Secure Role-Based Access**
- **Challenge**: Different access levels for users
- **Solution**: RBAC roles in Snowflake + masking PII

### 4. **Performance Bottlenecks**
- **Challenge**: Large datasets caused delays
- **Solution**: Materialization strategies + Snowflake caching

---

## 📈 Results & Business Impact

- ✅ **360° Operational Insight** — Executive dashboards simplified high-level decision-making
- ✅ **Accelerated Expansion Strategy** — The owner had all KPIs in one place to guide the new hospital's integration
- ✅ **Data Governance** — Compliant, secure, and auditable solution
- ✅ **Scalable Analytics Foundation** — Future hospitals or systems can be added easily

---

## 🤝 Meet the Team

| Name       | Email                         |
|------------|-------------------------------|
| Srinadh    | iamsrinadh030@gmail.com       |
| Srinivas   | kommireddy5566@gmail.com      |
| Madan      | madankumardivve@gmail.com     |
| Priyanka   | iampriyankakandula@gmail.com  |

---

## 🛣️ Looking Ahead

The project was a **super hit**, and future enhancements are already in the works:

- Advanced dbt tests + Great Expectations
- Power BI Row-Level Security
- ML models for patient satisfaction prediction
- Integration with FHIR APIs for clinical data

> Stay tuned for version 2.0 🚀

---

## 📂 Repository Structure

Welcome to your new dbt project!

### Using the starter project

Try running the following commands:
- dbt run
- dbt test


### Resources:
- Learn more about dbt [in the docs](https://docs.getdbt.com/docs/introduction)
- Check out [Discourse](https://discourse.getdbt.com/) for commonly asked questions and answers
- Join the [chat](https://community.getdbt.com/) on Slack for live discussions and support
- Find [dbt events](https://events.getdbt.com) near you
- Check out [the blog](https://blog.getdbt.com/) for the latest news on dbt's development and best practices
