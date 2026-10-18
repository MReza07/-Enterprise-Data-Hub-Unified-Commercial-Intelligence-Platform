# -Enterprise-Data-Hub-Unified-Commercial-Intelligence-Platform
> A production-grade medallion data pipeline on Microsoft Fabric unifying **Salesforce**, **Shopify**, and **Google Analytics (GA4)** into a single Power BI dashboard with a Customer 360 view
> # Enterprise Data Hub: Unified Salesforce, Shopify & GA4 Analytics (Microsoft Fabric & Power BI)

An end-to-end data engineering and business intelligence project built on **Microsoft Fabric**. This solution unifies multi-source data across e-commerce transactions (**Shopify REST API**), digital marketing web traffic (**Google Analytics 4**), and CRM relationship pipelines (**Salesforce Dataflow Gen2**) using a medallion architecture (`Bronze` -> `Silver` -> `Gold`), transformed with **PySpark** and **Dataflow Gen2**, modeled into an enterprise star schema, and visualized in **Power BI** across four comprehensive executive dashboard suites.

> **Data note:** This project integrates multi-source enterprise data streams to simulate cross-functional business analysis, covering storefront e-commerce metrics, multi-channel web analytics session tracking, and CRM sales pipelines.

---

## Dashboard preview

| Executive Overview | Sales Pipeline |
|---|---|
| ![Executive Overview](Executive%20Overview.jfif) | ![Sales Pipeline](Sales%20Pipeline.jfif) |

| Marketing & Web Analytics | Customer 360 View |
|---|---|
| ![Marketing & Web Analytics](Marketing%20&%20Web%20Analytics.jfif) | ![Customer 360](Customer%20360.jfif) |

---

## Data pipeline

```mermaid
flowchart LR
    A1["Shopify REST API"] -->|"PySpark"| B1["Bronze Layer<br/>sp_orders, sp_customers, sp_products"]
    A2["GA4 Notebook Simulator"] -->|"PySpark"| B2["Bronze Layer<br/>ga4_sessions"]
    A3["Salesforce"] -->|"Dataflow Gen2"| B3["Bronze Layer<br/>Accounts, Contacts, Leads, Opportunities"]
    
    B1 & B2 & B3 --> C["Silver Layer<br/>Cleaned, Standardized & Bridged via Email"]
    C --> D["Gold Layer<br/>Star Schema Dimensions & Facts"]
    D --> E["Power BI Direct Lakehouse<br/>4-Page Executive Dashboard"]
