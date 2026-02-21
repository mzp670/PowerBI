# 🚴‍♂️ Adventure Works Manufacturing Quality Dashboard
### *Power BI Project – Defect Analytics & Production Insights*

## 📌 What Have I Been Working On?
For the past while, I’ve been building an **interactive Power BI dashboard** designed to uncover manufacturing defects in Adventure Works’ bike assembly line. This project transforms raw production data into **operational style insights** that highlight trends, pinpoint root causes, and reveal quality‑improvement opportunities.

The mission is simple:  
To give operational teams a fast, intuitive view of **where defects occur, why they occur, and how to fix them** before products ever reach the customer.

---

## 🎬 Dashboard Preview  
---
The report contains **two key analytical sections**, each revealing a different angle on manufacturing quality.

---

## 🔹 1. Production Quality & First‑Pass Yield
This tab focuses on **how many bikes pass inspection the first time**, without any rework or touch‑ups—an essential measure of production efficiency.

![PBI Bike Lowres](Asset_Repo/PBI%20Bike%20Lowres.gif)

### **Key Insights**
- **First‑Pass Yield (FPY):** Percentage of units passing on the first attempt  
- **Success Rate vs. Defects:** Comparison of good vs. failed units per job order  
- **Defect Trend Analysis:** How defect counts shift over time  
- **Category Trend Analysis:** Identification of bike type with recurring defects

### **This tab helps answer:**
- Is overall product quality improving or declining?  
- Which shifts or line show instability?  
- How severe are the breakdown points in production?
  
---

## 🔹 2. Defect Stages, Fault Patterns & Cost Impact  
This section dives deeper into **where defects originate**, **which types are most common**, and **how costly they are** to the business.

![PBI Bike Fault Lowres](Asset_Repo/PBI%20Bike%20Fault%20Lowres.gif)

### **Key Insights**
- **Defect Location Mapping:** Assembly stages with the highest concentration of failures  
- **Common Fault Types:** Repeated issues (alignment problems, assembly mistakes, finishing defects, etc.)  
- **Inspection Highlights:** Summary of pass/fail rates across inspection points  
- **Cost of Quality:** Repair and scrap costs broken down by defect type and bike category  

### **This tab helps answer:**
- Which assembly stages require immediate attention?  
- Are defects driven by operator error, equipment wear, or supplier problems?  
- How much is poor quality costing us per product line?

---

## 🧠 Why Track Failure or Defect Rates?
Finding the failure or defect rate in a production report is essential because it tells you how **healthy, efficient, and profitable** your manufacturing process really is. Defect rate shows you how many products fail to meet standards prior release to customer. It is important to set quality standards before any item release to prevent customer complaints resulting to customer attrition.

By tracking which stages or components cause the most defects can help **identify root causes early**. Maybe the machine needs maintenance, or there is a requirement to increase staff due to burnout. It can also be caused by supplier issues.

This reasons and more can assist the company to reduce any arising cost resulting to defects at the early stage. Imagine the cost of rework, scrapping or double shipping due to return? Most importantly, **we want our customers happy**. We are proud of our products and the way we build them so quality output is necessary to maintain customer satisfaction. 

### Some Tricky Parts

**Relationship Management:**  
Power BI relationships can be helpful, confusing, or outright mischievous—especially when unnecessary links cause ambiguity. For slicers to behave as expected, only intentional, clean relationships should exist. A tidy model equals a tidy mind, and far fewer “Why is this filtering everything except what I want?” moments.

**Top 3 Technician Findings:**  
Getting the top three findings per model and defect location sounded simple… until it wasn’t. Computing it purely in DAX was fun, but the results weren’t consistent enough for what I needed. To keep the file lean (and my sanity intact), I shifted the logic into Power Query—adding a ranking column and applying targeted filters. Not the only way to do it, but definitely the most reliable at this stage.

```powerquery
/Table.Group(
    SortedRows,
    {"Defect Date", "Bike Type", "Defect Location"},
    {
        {
            "RankedData",
            each Table.AddRankColumn(
                _,
                "Rank",
                {
                    {"Defect Date", Order.Ascending},
                    {"Bike Type", Order.Ascending},
                    {"Product ID", Order.Descending}
                },
                [RankKind = 1]
            )
        }
    }
)

