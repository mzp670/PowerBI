# 🏭 Assembly Hold Report Dashboard  
---
Most assembly hold trackers begin their life in Excel — practical, reliable, and functional. But while Excel can absolutely present the numbers, this project demonstrates how Power BI elevates the same tracker into a clearer, more compelling operational story.


## 🎬 Dashboard Preview  
---

![PBI Bike AH](Asset_Repo/PBI%20Bike%20AH.gif)

This dashboard visualizes the **year-on-year total number of assembly holds raised**, providing a quick quality-performance snapshot of manufacturing operations. It highlights which year experienced the **highest volume of delays** and allows stakeholders to immediately identify patterns and trends.

Beyond volume tracking, the dashboard surfaces key performance indicators such as **total holds** raised and the **average turnaround time** to resolution. Measuring issues is important — resolving them efficiently is what truly reflects operational maturity.

Additional visuals provide insight into who raised the issues and where they occurred, adding ownership and accountability to the data. For deeper visibility, the dashboard also includes a detailed view of in-progress reports alongside recently completed cases, ensuring both leadership and operations teams can see what requires attention.

By transforming a traditional tracking file into an interactive Power BI report, this project showcases how thoughtful visualization can turn routine reporting into meaningful insight.

---
### Some Tricky Parts

- **Tooltips: small box, big brain energy.** In **Microsoft Power BI**, tooltips are an underrated way to sneak in extra insights without overcrowding your main visual. They let you add deeper granularity—think breakdowns, trends, or even mini visual summaries—while keeping your report clean and focused. The tricky (but fun) part is managing filter context. Depending on your design goal, you can override or remove filters from the main visual to show broader comparisons (like overall averages), or keep them tightly scoped for precision. It’s basically giving your chart a secret second personality.

<p align="center"><img src="Asset_Repo/AH_Tooltip.jpg" width="500"/></p>


- **Dynamic narrative: because charts deserve a hype narrator.** Sometimes visuals are too high-level, other times they’re buried in detail—so adding a dynamic, filter-aware summary bridges the gap. Using measures tied to slicer selections, the dashboard automatically highlights the months with the highest and lowest assembly hold reports and calculates the year-over-year percentage increase or decrease. The result? A smart narrative that surfaces key takeaways instantly—no detective work required.

<p align="center"><img src="Asset_Repo/AH_Narrative.jpg" width="500"/></p>

---
