# 🚚 Freight & Route Analysis Dashboard

> An end-to-end supply chain analytics project analyzing freight operations across carriers, routes, and shipment patterns using Excel and Power BI.

---

## 📌 Project Overview

This project analyzes a real-world logistics dataset to uncover operational insights around carrier performance, route concentration risk, shipment delays, and freight weight distribution. It simulates the kind of analysis a Supply Chain Analyst or Logistics Operations role would perform day-to-day.

**Tools Used:** Microsoft Excel · Power BI Desktop  
**Dataset:** Supply Chain Logistics Problem Dataset — Brunel University (public)  
**Domain:** Logistics & Operations · Freight Management · Supply Chain Analytics

---

## 🎯 Business Questions Answered

1. Which carrier handles the most volume — and which delays the most?
2. How concentrated is the freight network across routes?
3. What is the overall on-time delivery performance?
4. How is shipment weight distributed across carriers?

---

## 📊 Dashboard KPIs

| Metric | Value |
|---|---|
| Total Orders Analyzed | 9,215 |
| On-Time Delivery Rate | 97.92% |
| Average Transit Time | 1.72 days |
| Total Freight Weight | 183,117 KG |
| Routes Identified | 3 |
| Carriers Analyzed | 3 |

---

## 🔍 Key Findings

### 1. Carrier Performance
- **V444_0** is the dominant carrier, handling **68% of all orders** (6,264 shipments)
- **V44_3** has a **perfect on-time record** across its 854 orders
- **V444_0** carries the highest delay risk despite being the most utilized carrier

### 2. Route Concentration Risk
- **PORT04 → PORT09** accounts for **98.11% of all shipments** (9,041 orders, 150,947 KG)
- Extreme dependence on a single lane represents a significant supply chain vulnerability
- PORT05 → PORT09 is virtually unused (1 order), suggesting an untapped alternative route

### 3. Delivery Performance
- Overall on-time rate of **97.92%** across all service levels
- **DTP service level** accounts for the bulk of volume (6,218 orders)
- Near-universal delay flags suggest aggressive service level targets in the network

### 4. Shipment Weight Distribution
- **Heavy shipments dominate** across all three carriers
- V444_0 handles the largest share of both Medium and Heavy freight
- V44_3 specializes almost entirely in Heavy category shipments

---

## 🗂️ Project Structure

```
freight-route-analysis/
│
├── data/
│   └── Supply_chain_logistics_problem.xlsx   # Raw dataset
│
├── excel/
│   └── SCM_Analysis_Workbook.xlsx            # Cleaned data + pivot tables
│
├── powerbi/
│   └── Freight_Route_Analysis.pbix           # Power BI dashboard
│
└── README.md
```

---

## ⚙️ Excel Work — Phase 1

**Data Cleaning:**
- Verified 9,215 rows with zero null values
- Standardized carrier and port naming conventions

**Calculated Columns Added:**
| Column | Logic |
|---|---|
| Delay Flag | IF(Ship Late Day count > 0, "Delayed", "On Time") |
| Weight Category | Light (<100 KG) / Medium (<500 KG) / Heavy (500+ KG) |
| Route | Concatenation of Origin Port → Destination Port |

**Pivot Tables Built:**
1. Carrier Performance — order count + average late days by carrier
2. Route Volume — order count + total weight by route
3. Delay by Service Level — on-time vs delayed split across CRF, DTD, DTP

---

## 📈 Power BI Dashboard — Phase 2

**4 Visuals built:**
1. **KPI Cards** — Total Orders, On Time %, Avg Transit Days
2. **Carrier Performance Bar Chart** — Orders by carrier, split by Delay Flag
3. **Route Volume Donut Chart** — Share of shipments by route
4. **Weight Category Column Chart** — Shipment weight distribution by carrier

**DAX Measure Created:**
```dax
On Time % = 
DIVIDE(
    COUNTROWS(FILTER(OrderList, OrderList[Delay Flag] = "On Time")),
    COUNTROWS(OrderList)
) * 100
```

---

## 💡 Recommendations

1. **Diversify carrier dependency** — V444_0 handling 68% of volume creates a single point of failure
2. **Investigate PORT04 → PORT09 concentration** — develop alternative routing via PORT05 to reduce lane risk
3. **Review service level agreements** — near-universal delay flags suggest SLA targets may need recalibration
4. **Leverage V44_3's reliability** — with a perfect on-time record, consider scaling its volume

---

## 👤 About

**Aniket Jantli**  
BBA — Logistics & Supply Chain Management | Finance  
Rani Channamma University, Belagavi  
Certifications: CSCMP Supply Chain Essentials · Google Data Analytics · Lean Six Sigma Yellow Belt

[LinkedIn](https://linkedin.com/in/) · [GitHub](https://github.com/)

---

*This project was built as part of a self-directed supply chain analytics portfolio.*
