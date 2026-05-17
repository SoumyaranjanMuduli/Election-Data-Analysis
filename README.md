# 🗳️ India Election Analysis — Power BI

> **Power BI political data analysis project** examining India's general election results — seat distribution, party alliances, vote share, state-wise performance, and coalition dynamics — with custom DAX measures for alliance grouping.

---

## 📌 Project Overview

India's elections involve hundreds of parties, complex alliances, and results across 543 Lok Sabha constituencies. This project cuts through the complexity to answer:

- How did seats distribute across parties and alliances?
- Which states drove the majority of wins for each major alliance?
- How does vote share compare to actual seat count — where did votes "waste"?
- What is the seat tally for NDA, INDIA Alliance, and Others?
- How did results shift compared to the previous election?

---

## 🗂️ Repository Structure

```
📦 india-election-analysis
 ┣ 📁 Images/                        # Dashboard screenshots
 ┣ 📁 Raw Data/                      # Source election data files
 ┣ 📊 Election Analysis.pbix         # Power BI dashboard (5,494 KB)
 ┣ 📄 Party Alliance DAX.txt         # DAX measures for alliance grouping logic
 ┗ 📄 README.md
```

---

## 🔧 Tools Used

| Tool | Purpose |
|---|---|
| **Power BI Desktop** | Dashboard, data modeling, DAX |
| **DAX** | Custom alliance classification, vote share calculations |
| **Excel / CSV** | Raw election result data |

---

## 🧮 Key DAX Logic — Party Alliance Grouping

The `Party Alliance DAX.txt` file contains the core measure that classifies individual parties into alliance buckets (NDA / INDIA / Others). This is the most technically complex part of the project — a SWITCH or CONTAINSSTRING-based DAX measure that maps party names to alliance labels dynamically.

```dax
-- Example structure (see Party Alliance DAX.txt for full measure)
Alliance =
SWITCH(
    TRUE(),
    CONTAINSSTRING([Party], "BJP") || CONTAINSSTRING([Party], "JDU"), "NDA",
    CONTAINSSTRING([Party], "INC") || CONTAINSSTRING([Party], "SP"), "INDIA Alliance",
    "Others"
)
```

---

## 📊 Dashboard Highlights

**KPI Cards**
- Total Seats Contested
- Total Seats Won — NDA
- Total Seats Won — INDIA Alliance
- Total Seats Won — Others

**Visuals**
- Seat distribution by alliance (donut/bar chart)
- State-wise winning party map (filled map or matrix)
- Vote share vs. seats won comparison (scatter / bar)
- Top 10 parties by seats won (horizontal bar)
- Alliance seat tally trend vs. previous election
- Margin of victory distribution (how close were the races?)
- Constituency-level results table with filters

**Slicers**
- State
- Alliance
- Party
- Margin category (Safe / Competitive / Razor-thin)

---

## 💡 Key Insights

- The gap between **vote share and seat share** highlights how India's first-past-the-post system amplifies or suppresses party representation
- Several states show **clean sweeps** by a single alliance — examining these reveals regional political dominance patterns
- Razor-thin margin constituencies (won by < 5,000 votes) could have flipped the overall alliance tally
- "Others" category — independent and regional parties — holds significant power as kingmakers in a hung parliament scenario
- Urban vs. rural constituency results show distinct voting patterns across alliances

---

## 🚀 How to Use

1. Open **Power BI Desktop**
2. Load raw data files from the `Raw Data/` folder
3. Open `Election Analysis.pbix`
4. Import DAX measures from `Party Alliance DAX.txt` if building from scratch
5. Refresh data source

---

## 👤 Author

**[Your Name]**
[LinkedIn](https://linkedin.com/in/yourprofile) · [Portfolio](https://yourportfolio.com) · [Email](mailto:you@email.com)

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

*Election data sourced from publicly available Election Commission of India results. Used for educational and analytical purposes only.*
