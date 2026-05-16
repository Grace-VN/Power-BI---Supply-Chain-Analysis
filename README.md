# Power-BI---Supply-Chain-Analysis
📊 Supply Chain Make vs Buy Scenario Analysis

A complete end-to-end supply chain analytics project built in Microsoft Power BI to support Make vs Buy decision-making using dynamic scenario analysis, supplier evaluation, manufacturing capacity planning, and quality-adjusted cost modeling.

📌 Project Overview

This project simulates a real-world supply chain case study for a fictional company, Tenate Industries, which manufactures replacement parts for industrial pizza ovens.

The objective is to determine whether the company should:

Buy components from external suppliers
or Make them internally

The project evolves through 3 major analytical stages:

Buy Option Analysis
Scenario Planning & Volume Analysis
Make vs Buy Optimization

The final solution combines:

Supplier quote analysis
Dynamic production-volume simulation
Manufacturing capacity planning
Capital investment analysis
Supplier quality/yield adjustments
Row-level security (RLS)
🧩 Project Structure
1️⃣ Buy Option Analysis
🎯 Objective

Evaluate supplier quotes and identify the lowest total procurement cost for each product and volume combination.

📌 Key Concepts
Supplier Quotes

Each supplier quote includes:

Part Number
Supplier Name
Minimum Production Volume
Unit Cost
Non-Recurring Expenses (NRE)
Extended Cost

Calculated as:

Extended Cost = Unit Cost × Volume

Represents only the product purchasing cost.

Full Cost

Calculated as:

Full Cost = Extended Cost + Non-Recurring Expenses

Represents the total procurement cost.

📊 Visualizations Built
Supplier quote comparison tables
Unit cost vs volume line charts
Non-recurring expense trend charts
Lowest-cost supplier card visualization
Cost breakdown stacked bar chart
Interactive slicers for:
Part Number
Volume
🛠 DAX & Modeling
Calculated columns for:
Extended Cost
Full Cost
Bottom-N filtering for supplier selection
Interactive report behavior using Edit Interactions
🔍 Key Insight

Supplier pricing behavior changes significantly with production volume. The lowest unit cost supplier is not always the lowest full-cost supplier due to non-recurring expenses.

2️⃣ Scenario Planning & Volume Analysis
🎯 Objective

Build a dynamic scenario analysis tool that evaluates supplier costs for production volumes beyond quoted values.

📌 Business Challenge

Real-world demand is uncertain. Companies rarely order exact quoted volumes, so decision-makers need flexible cost simulation tools.

⚙️ Scenario Volume Parameter

Created a dynamic numeric parameter:

Range: 1,000 → 100,000 units
Increment: 500 units
Controlled via slicer

This allows real-time demand simulation.

📌 Dynamic Cost Measures
Scenario Full Cost

Built using:

MINX()
FILTER()

The model:

Evaluates all eligible supplier quotes

Filters quotes where:

Quote Volume <= Scenario Volume
Returns the minimum valid full cost
📈 Advanced Visualizations
Dynamic supplier cost trend line charts
Volume-based cost comparison
Scenario reference constant line
Lowest-cost supplier KPI card
🔐 Row-Level Security (RLS)

Implemented security roles:

Project Siliode Team Member
Project Kerfuffle

Users only see project-specific records.

🔍 Key Insight

Supplier competitiveness changes dramatically across production volumes. Scenario-based planning enables more accurate procurement strategies than static quote analysis.

3️⃣ Make vs Buy Optimization
🎯 Objective

Compare internal manufacturing costs against supplier procurement costs to determine the optimal sourcing strategy.

🏭 Internal Manufacturing Analysis
📌 Internal Manufacturing Data

Internal estimates include:

Cost per Unit
Existing Manufacturing Capacity
Machine Capacity
Machine Investment Cost
Machine Model
📌 Incremental Cost Logic

The project distinguishes between:

Sunk Costs → ignored
Incremental Costs → included

Only new investments required to meet demand are considered.

⚙️ Capacity Gap Analysis
Additional Capacity Required

Calculated as:

Additional Capacity Required =
Scenario Volume - Existing Capacity

If existing capacity exceeds demand:

Required Capacity = 0
⚙️ Equipment Investment Calculation
Machines Required

Calculated using:

Machines Required =
ROUNDUP(
Additional Capacity Required / Unit Capacity per Machine
)
Capital Investment Required
Capital Investment =
Machines Required × Machine Fixed Cost
📌 Make Scenario Full Cost
Make Full Cost =
(Unit Cost × Scenario Volume)
+ Capital Investment Required
⚖️ Make vs Buy Decision Engine
📌 Decision Logic

The report dynamically recommends:

Make
or Buy

Based on whichever option has lower total cost.

📌 Cost Avoidance Measure
Cost Avoidance =
ABS(
Make Scenario Full Cost
-
Buy Scenario Full Cost
)

Quantifies savings from the recommended decision.

🧪 Supplier Quality & Yield Adjustment
📌 Business Enhancement

The quality team identified poor supplier yield rates:

Supplier	Yield Rate
Widgetmakers, Inc	72%
Ringo Nova	83%
Other Suppliers	98%
📌 Yield-Adjusted Purchasing

To meet production demand:

Required Order Quantity =
Scenario Volume / Yield Rate

This adjusts procurement cost for defective units.

🔍 Key Insight

Supplier quality significantly impacts actual procurement cost. A lower-priced supplier may become more expensive after accounting for defects and yield loss.

📊 Dashboard Features
Dynamic Scenario Volume slicer
Supplier selection dashboard
Cost trend analysis
Make vs Buy recommendation engine
Cost avoidance KPI
Manufacturing capacity planning
Quality-adjusted supplier comparison
Row-level security
🛠 Tools & Technologies
Microsoft Power BI
DAX (Data Analysis Expressions)
Iterative Functions:
MINX()
FILTER()
ROUNDUP()
FIRSTNONBLANK()
Data Modeling
Scenario Parameters
Row-Level Security (RLS)
📷 Dashboard Preview

(Add screenshots here)

Suggested screenshots:

Supplier Selection Dashboard
Scenario Analysis Page
Make vs Buy Comparison
Cost Trend Line Charts
Manufacturing Capacity Analysis
🚀 How to Use
Download SCM analysis.pbix
Open in Power BI Desktop
Adjust the Scenario Volume slicer
Explore:
Supplier rankings
Full cost analysis
Make vs Buy recommendations
Capacity investment impacts
Yield-adjusted procurement costs
📌 Business Value

This project demonstrates how supply chain analytics can support:

Procurement optimization
Manufacturing planning
Capital investment decisions
Demand uncertainty management
Supplier quality evaluation

The solution transforms static quote analysis into a dynamic decision-support system.

⭐ Future Improvements
Demand forecasting integration
Monte Carlo simulation
Supplier lead-time analysis
Sustainability scoring
Automated data refresh pipelines
Deployment to Power BI Service