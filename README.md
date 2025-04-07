# Data Analysis Report: Energy Performance & Fuel Utilization by Electricity Market Structure

This comprehensive report delves into how efficiently energy is generated (Thermal Efficiency), the total output of that generation (Gen_MMBtu), and the corresponding fuel consumption (Fuel_MMBtu). The Power BI dashboard provides interactive slicers, toggles, and a map to explore data from 2011 to 2024, segmented by both fuel categories and market structures (Competitive, Hybrid, Monopoly).

---

## Executive Summary

This analysis aims to offer clear insights into operational performance, highlighting:

- **Thermal Efficiency**: How effectively fuel is converted to electricity.
- **Total Generation**: The scale of power output in MMBtu.
- **Total Fuel Consumption**: The energy content of the fuel used, also in MMBtu.
- **Market Structures**: The influence of competitive, hybrid, and monopoly markets on efficiency and fuel usage.

Key features include the ability to:
- Select any year within **2011–2024** to see real-time updates on major KPIs.
- Compare **KPI**s and **Year-Over-Year (YOY) % changes**.
- Toggle between **KPI**s for each **Market Structure** using interactive buttons.
- Toggle between **Total Generation** and **Fuel Consumption** by fuel category.
- Explore a **US map** to filter or highlight specific states based on market type.

Overall, the dashboard fosters data-driven decision-making by showcasing trends in efficiency, fuel usage, and generation mix across different time periods and regulatory environments.

---

## Introduction

- **Purpose:**  
  The analysis evaluates energy generation efficiency, fuel usage patterns, and long-term trends using data from an interactive “Energy Performance & Fuel Utilization” dashboard.

- **Data Source:**  
  - Extracted via the EIA API, covering **2011–2024**.
  - Processed in Python (pandas, numpy) and refined in Power BI.
  - Includes aggregated columns (e.g., Fuel_MMBtu, Gen_MMBtu) and custom categories (e.g., Fossil Fuels, Renewables).

- **Scope:**  
  1. **Key KPIs:** Thermal Efficiency, Total Generation, Total Fuel Consumption.  
  2. **Time Range:** ~2011 to 2024 (with slicers).  
  3. **Fuel Category Breakdown:** Fossil Fuels, Renewables, Nuclear, Other/Storage, etc.  
  4. **Market Type Distribution:** Competitive, Hybrid, Monopoly, selectable on a US map.

> ![Screenshot 2025-04-05 162852](https://github.com/user-attachments/assets/d020111b-e191-4ffc-95f4-df50b7566fe4)


---
## Data Preparation & Transformation

Over 175,000 rows of data were collected, covering multiple years and diverse fuel types. The raw dataset included **Year** (extracted from "Period"), **location** (state), **fuelTypeDescription**, and **consumption** metrics in various units. Below is an overview of how the data was cleaned and enhanced in Python and Power BI.

1. **Python Cleaning (pandas, numpy)**  
   - **Unit Standardization**: Converted consumption values (originally in thousand short tons and thousand physical units) into a single format (thousand physical units).  
   - **Market Structure Assignment**: Grouped states into **monopoly**, **competitive**, or **hybrid** for comparative analysis.

2. **Power Query Custom Columns**  
   - **Generation to MMBtu**: Converted thousand MWh to MMBtu using a custom column.  
   - **Heat Content Adjustment**: Unified heat content to Btu per short ton for consistent fuel-energy calculations.  
   - **Fuel Category**: Used a “let” expression to classify detailed fuel types (e.g., Fossil Fuels, Renewables) for simpler, high-level comparisons.  
   - **Fuel_MMBtu Calculation**:  
     \[
       \text{Fuel\_MMBtu} = \frac{(\text{consumption-for-eg} \times 1000) \times [Adjusted\_HeatContent]}{1{,}000{,}000}
     \]
     Ensures all fuel usage is measured in MMBtu.

### Why It Matters

- **Consistency & Comparability**: Having both **Gen_MMBtu** and **Fuel_MMBtu** standardizes analysis, making efficiency calculations straightforward.  
- **Streamlined Visualization**: Grouping fuel types into categories and assigning market structures helps quickly identify trends and compare performance across regions and regulatory environments.  
- **Reliability**: Clear, uniform data fosters confidence in the dashboard’s insights, enabling data-driven decisions on energy operations and policy.
---

## Key Findings (Dashboard Interactivity)

The Power BI report offers dynamic controls to explore the data in multiple ways:

1. **Interactive Year Slicer (2011–2024)**  
   - Select any year to instantly update KPI cards, charts, and the map.

2. **Dynamic KPI Cards with YOY % Changes**  
   - A toggle button switches the display between **raw KPI values** and **Year-Over-Year (YOY%) changes**, so users can see if each metric has increased or decreased relative to the prior year.

3. **Fuel Category & Market Structure Buttons**  
   - **Market Structure (Competitive, Hybrid, Monopoly):** Filtering reveals how regulatory environments may shape efficiency and fuel usage.  
   - **Fuel Category Toggle (Gen vs. Fuel):** The stacked area chart can display **Total Generation (MMBtu)** or **Fuel Consumption (MMBtu)** by category, clarifying how various fuel types evolve over time.

4. **Map for Geographical Insights**  
   - Each state is color-coded by its **market type**. Selecting a state filters the entire dashboard to its data, enabling deeper regional analysis.

5. **Trend Observations**  
   - **Over Time:** Users can see if renewables are gaining ground or whether fossil fuels dominate.  
   - **Efficiency vs. Fuel:** Switching between total fuel consumption and generation highlights whether higher output is fueled by proportional increases in consumption or more efficient processes.

6. **Example (2013)**  
   - KPIs for 2013 can be examined, but any other year’s data can be similarly accessed, allowing immediate comparison across the entire 2011–2024 range.

This interactivity empowers stakeholders to perform multifaceted analyses, comparing different market structures, time periods, and fuel categories in a single, unified platform.

---

## Energy Generation & Fuel Consumption Trends (Time Series Analysis)

- **Overall Trend (2011–2024):**  
  Use the stacked area chart to see whether **Gen_MMBtu** is increasing, decreasing, or stable over the selected timeframe.

- **Fuel Category Breakdown:**  
  - Fossil Fuels, Renewables, Nuclear, Other/Storage show varying contributions to total generation.  
  - Identify if renewables are growing or if a particular fossil fuel dominates.

- **Comparing Generation & Fuel:**  
  - By toggling to **Fuel (MMBtu)** in the stacked chart, see how fuel consumption correlates with generation output (potentially revealing efficiency shifts over the years).

> ![Screenshot 2025-04-07 023422](https://github.com/user-attachments/assets/ab6ff959-f296-4a12-9236-483d835b2e84)


---

## Market Type Analysis

- **US Map Visualization:**  
  - States are grouped into **Competitive, Hybrid, Monopoly** markets.  
  - Clicking on a state filters the dashboard to show local KPIs, letting you compare states or regions.

- **Performance by Market Structure:**  
  - Thermal Efficiency and Fuel Usage can be contrasted between states under different regulatory setups.  
  - The slicer and button functionality reveals how each market segment might outperform or underperform in key metrics.

> ![Screenshot 2025-04-07 023753](https://github.com/user-attachments/assets/2b9284fd-163c-426c-bc67-470ab5140612)


---

## Efficiency Insights

- **Thermal Efficiency:**  
  - Ties generation to fuel usage; higher efficiency means less fuel is required to produce a given amount of energy.  
  - Look for YOY % changes to identify improvements or declines in plant operational performance.

- **Factors Influencing Efficiency:**  
  - Technological upgrades, switching from coal to natural gas, or adopting renewables.  
  - Market competition can drive investments that enhance efficiency, whereas monopoly regions might lag.

---

This end-to-end analysis ensures that policymakers, plant operators, and other stakeholders have the information needed to optimize energy performance and strategize around ever-changing fuel and market dynamics.
